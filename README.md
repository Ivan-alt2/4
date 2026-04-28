from typing import List

def min_platforms(weights: List[int], limit: int) -> int:

    # Сортируем веса по возрастанию
    weights.sort()
    n = len(weights)
    platforms = 0
    left = 0  # указатель на самого лёгкого робота
    right = n - 1  # указатель на самого тяжёлого робота

    while left <= right:
        # Если самый тяжёлый и самый лёгкий роботы могут ехать вместе
        if weights[left] + weights[right] <= limit:
            # Размещаем их на одной платформе
            left += 1  # берём следующего лёгкого робота
            right -= 1  # берём следующего тяжёлого робота
        else:
            # Самый тяжёлый робот едет один (лёгкий пока остаётся)
            right -= 1

        platforms += 1  # увеличиваем счётчик платформ

    return platforms

# Чтение входных данных
weights_input = list(map(int, input().split()))
limit_input = int(input())

# Вычисление и вывод результата
result = min_platforms(weights_input, limit_input)
print(result)

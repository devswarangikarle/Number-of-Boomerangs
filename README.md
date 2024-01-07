# Number-of-Boomerangs

class Solution:
    def numberOfBoomerangs(self, points):
        def distance(p1, p2):
            return (p1[0] - p2[0]) ** 2 + (p1[1] - p2[1]) ** 2

        def countBoomerangs(p, distances):
            count = 0
            for dist, freq in distances.items():
                if freq >= 2:
                    count += freq * (freq - 1)
            return count

        total_boomerangs = 0

        for i in range(len(points)):
            distances = {}
            for j in range(len(points)):
                if i != j:
                    dist = distance(points[i], points[j])
                    distances[dist] = distances.get(dist, 0) + 1

            total_boomerangs += countBoomerangs(points[i], distances)

        return total_boomerangs


solution = Solution()

points1 = [[0,0],[1,0],[2,0]]
print(solution.numberOfBoomerangs(points1)) 

points2 = [[1,1],[2,2],[3,3]]
print(solution.numberOfBoomerangs(points2))  

points3 = [[1,1]]
print(solution.numberOfBoomerangs(points3)) 

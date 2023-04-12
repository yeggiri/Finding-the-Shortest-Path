# Finding-the-Shortest-Path
가장 짧은 경로를 계산하는 코드
import matplotlib.pyplot as plt
import heapq

def dijkstra(graph, start_node, end_node):
    distances = {node:float('inf') for node in graph}
    distances[start_node] = 0
    
    pq = [(0,start_node)]
    
    while pq:
        current_distance, current_node = heapq.heappop(pq)
        
        if current_node == end_node:
            path = []
            while current_node in predecessors:
                path.append(current_node)
                current_node = predecessors[current_node]
            
            path.append(start_node)
            path.reverse()
            return path, distances[end_node]
        
        for neighbor, weight in graph[current_node].items():
            distance = current_distance + weight
            
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                predecessors[neighbor] = current_node
                heapq.heappush(pq,(distance, neighbor))
                
    return None
            

graph = {
    'A' : {'B':4,'C':4},
    'B' : {'A':4, 'D':2},
    'C' : {'A':4,'D':2},
    'D' : {'B':2,'C':2}   
    }

start_node = 'A'
end_node = 'D'
predecessors = {}


path, shortest_distance = dijkstra(graph, start_node, end_node)
print(f"The shortest path from {start_node} to {end_node} is: {path}")
print(f"The shortest distance is: {shortest_distance}")

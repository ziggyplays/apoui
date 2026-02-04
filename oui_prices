from ouigo import Ouigo
import csv
from datetime import datetime, timedelta

api = Ouigo(country="FR")

routes = [
    ("Paris", "Toulouse"),
    ("Paris", "Bordeaux"),
]

today = datetime.today()

with open("prices.csv", "a", newline="", encoding="utf-8") as file:
    writer = csv.writer(file)

    for i in range(0, 30):  # 30 jours à venir
        date = (today + timedelta(days=i)).strftime("%Y-%m-%d")

        for origin, dest in routes:
            trips = api.find_travels(origin=origin, destination=dest, outbound=date)

            for t in trips:
                writer.writerow([
                    datetime.now().strftime("%Y-%m-%d %H:%M"),
                    origin,
                    dest,
                    date,
                    t.departure_timestamp,
                    t.price
                ])

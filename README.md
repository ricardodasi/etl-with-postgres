# etl-with-postgres


#etl part
df = df[df['page'] == 'NextSong']
df.head()


t = pd.to_datetime(df['ts'], unit = 'ms')

t.head()


time_data = [t,t.dt.hour,t.dt.day,t.dt.weekofyear,t.dt.month,t.dt.year,t.dt.weekday]

column_labels = ['timestamp', 'hour', 'day', 'week_of_year', 'month', 'year', 'weekday']

time_df = pd.DataFrame(dict(zip(column_labels,time_data )))
time_df.head()

for i, row in time_df.iterrows():
    print(time_table_insert)
    print(list(row))
    cur.execute(time_table_insert, list(row))
    conn.commit()


#Queries part 


time_table_create = ("""
CREATE TABLE IF NOT EXISTS time (
    start_time TIMESTAMP NOT NULL
        , hour INT
        , day INT
        , week INT
        , month INT
        , year INT
        , weekday INT
)
""")



time_table_insert = ("""
INSERT INTO time (start_time, hour, day, week, month, year, weekday)
VALUES(%s, %s, %s, %s, %s, %s, $s)
""")



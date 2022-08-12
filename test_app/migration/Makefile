postgres:
	docker run --name some-postgres -p 5000:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=mysecretpassword -d postgres
createdb:
	docker exec -it some-postgres createdb --username=root --owner=root simple_bank

migrateup:
	./migrate -path /home/mos/Documents/code_learn/go/backend_consp/test_app/migration -database "postgresql://root:mysecretpassword@192.168.88.187:5000/simple_bank?sslmode=disable" -verbose up

migratedown:
	./migrate -path /home/mos/Documents/code_learn/go/backend_consp/test_app/migration -database "postgresql://root:mysecretpassword@192.168.88.187:5000/simple_bank?sslmode=disable" -verbose down


dropdb:
	docker exec -it some-postgres dropdb -username=root --owner=root simple_bank migrateup migratedown

.PHONY: postgres createdb  dropdb migrateup migratedown

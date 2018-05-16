### C Linked List

Made it the last year, works as expected with a good error handling.  

```c
struct s {
    int socket_fd;
} data = {
        .socket_fd = -1
};

static void custom_callback_for_each_elem(void *data) {
    struct s *casted = (struct s*) data;
    close(casted->socket_fd);
}

int main() {
    list_t list = list_init;

    list_add(&list, &data);

    for (iter_t *it = iter_begin(&list); it; iter_next(it)) {
        it->data;
    }

    list_remove(&list, list_at(&list, 0));
    list_add(&list, &data);

    if (!list_exists(&list, &data))
        raise_error("shouldnt appear\n");

    list_clear(&list, &custom_callback_for_each_elem);
    return 0;
}
```
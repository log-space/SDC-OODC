<p align="right">
	<b>Concept</b>
</p>

<hr/>

###### Tail Call
![s](https://user-images.githubusercontent.com/36118701/36640034-b9c60658-1a4a-11e8-8d11-0d30fb4adbbd.PNG)

```c
int save_data(data) {

	return input_data(data);
};

int input_data(data) {

	if (file_exist(data) == true) {
	
		return check_size(data);
	}
	else {
	
		return input_warning();
	}
};

int check_size(data) {

	...
	return check_mime_type(data);
};

int check_mime_type(data) {

	...
	return input_data_transaction(data);
};

int input_data_transaction(data) {

	...
	return 1;
};

int input_warning() {

	...
	return 0;
};
```

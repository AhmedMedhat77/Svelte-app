<script>
	import FilterUser from '../FilterUser/FilterUser.svelte';
	import NewUser from '../NewUser/NewUser.svelte';
	import SingleUser from '../SingleUser/SingleUser.svelte';
	import userImage from '../images/user.jpg';
	let users = [
		{
			id: '1',
			userName: 'Ahmed',
			userEmail: 'Ahmed@i.com',
			image:
				'https://thumbs.dreamstime.com/b/male-avatar-icon-flat-style-male-user-icon-cartoon-man-avatar-hipster-vector-stock-91462914.jpg',
			active: 'false'
		},
		{
			id: '2',
			userName: 'Mohamed',
			userEmail: 'Mohamed@i.com',
			image:
				'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARMAAAC3CAMAAAAGjUrGAAAAxlBMVEX////T1NgqKioGBgYfHx/+yJwAAADn5+rX2Ny6u78xMTIcHBuSkpaWl5rU1dkeHh4lJSXb3N8ZGRkTExP/zqEPDw8AAA/FxcUWFhbs7e709PT/yJyampqEhITPz8+QkJBpaWnxvpV2dnY5OTlOTk6xsbFhYWF/f3/LoX2lpaVBQUFISEi1troUGRzesIrBmXgAEBd9YEiGi5FaWloWHiNdUESFbVm2kXSVeGF1X00mHhhRRTo2LCKhgmc8NS9pVEIoGw6rhWSRFD1ZAAAKGklEQVR4nO2dC3uiOBfHFTDS2uFOBcZb7VVbW/d1t5ftzs7O9/9SbwIIQaIkSCUw+T8zbbWSh/Pz5JzDSaSdjpCQkJCQkJCQkJCQkJCQUL3yJ2eL0Wh0OzSDuk+FCwVP82tZtj3LsjxXtm6mk7rPqG4N74CtGFIqY+B6Y7Pu06pRt9cyzmMrHWx+V2c5k2wSkdBbwOZ39JX+DdFHUirjus/w5BqBQ0SQLOn3mkD+jVtAJHSVUd3neUJNXKUYCZR7V/eZnkwLQEUEarD06z7Z02hMjQTOH6Nf9+meQnOKUPKbQZnZLEggFK/1UGYeGxIIRWp5TJkzekkI5brus/5SjZliyVb6pu7z/kLRJ+Gs7PbW+cOSSCQJnNV97l+kfmkksKJtafJZFl31HZCxrPvsv0SzQXkkkuRN6z7/L9DtETMHSVbrtqBy9UtlYUwtrFIejwgmkey2dVNGx7qJ1LrcY1aARFJmdZtRqW6OnjlIoE0N2lu5CiSScVO3IdUpoOu+Fkse1m1KZRpbFTFpTzV7zHXOjuS2XAvOqpo60FEe6zamGk2qcxPoKO1IPZtK8nAsoxWrYJW6CaxR2lDM3lXpJpKkt6ANaVZTrqUy6rboeM2rSzqR3ManY7/aaCK1IcqOqiphU4Gm7xe9rjbCInm3dRt1nCZVR1ip+ZPnXq+eiWQ1e/JUP3Og3EZ3DLTc1DH+/DP6HkvZVfz8ISaDRi/15LPOX69vqzwIoiI0EOIuoGa32+6yO+lt8Ow4zgoZbNm27VkDIgzdsl0ZAFmW4c9/Pbx/7kIBddt1jM5jawzFcwG0Elz1eo4EzR7MxuP5bLO0AHA9HeMxgK+7vrv/tng6Gw6fZGX1ASn+7Q4yWOQG7zsPwqyjeNGbDhUy+YQM5Impqir8P3m6mJ3LCRXrcfrURc+rmqapZ0BZvTo95x/E005TmN3g8j4YGOh9lxOBZ8jkA04e+97shtIQmbNlDEVf9iGNbizzxlLWP0Im4cHA1SN3sZq8IijjQJBZL9DC9zW0HjypW9O7alfa+om7MLfPaubcVZQ1PKJnb0eBWNAlZaP7BV4WiQzgTOi9rGPr1dhTuo9WEk/kCxNNG001JxsYYpVL6FlX+ChA9gzlvm7DjtD5LpO/IZOry9B6sHmC08Y0u9+UFAmEcn1x1u0OFzPXCxMynGwvu6OAJjOZ7Vgjg4fed+ffKHpYQNrMZje2G0aStbFOMw/yhvABTDs952dulCYXbaOcNf9AG98uV3pciHiepeur1fpS+tF7Vy7XqxWemPUVZJidOtEoDc47HS1vDsqtbx+fyvoy0tr4/Pn+Bmu5ntN7fnv9+a+B/eYDxeSP/CCN7lODvD0fVz1YhvXg+48EvzvRw176Y/ob+P8tP4RUt1lH6T5nEIyQqEpJ9L23q+/Yd6f3gzBCk8uTTkfNW4RcxcmBIMt5zTsahNrwzyQ8EqAAVOJT6YqARAazuo06UkOio7zSOYrzTjy60REWaUk0i85R8lkYHdvkgi1SPh0ju37SOEq+WAsnXrO7saHmRCgPxVCcB+KRjW7GbkWMkzaFn9ikA+d1m1OJyGG2cPaQZ8553dZUpDERyo/DUJxfxGDS8NIk1TV7SCEGE9CiTcMBMaSA5/1QnGdiAduK+BrLZIRCRCKDhi+e74gcZ8GLk78E7IWdtdYjCYYjgwzlneQpsKQnvdqTNtNhCwo2qOB2g9rtu+3qmMrn1S4V5+qT+FJLGaCFouW3xn8Gzh8DEC307YEC3ns4FadHdhJ5sF03hTXKqNEZeQHSNb59UMDrc9Reg1+fXwERiYu3aS3Q5PtPZa510IrxHv33x6+Xh5dff/y37wU5klYDl4z7SN3pt4wu9up/kfb9+ltOF6N+rMZE3XiFU/1CJUurddtKq2TV9wSq21ZaCSZ5CSZ5CSZ5CSZ5CSZ5CSZ5CSZ5lWOiYRv8WsfEf2K2zfTjIj3wGYHWayq17lmZZJeAg377mPjgjIlJ/ho3YPCVGgwsoTEbE2KHiN5VTm1dKfmAicmephk1lNMaV1Jjl4XJ3t0ktNPnlKaVlQ90BiYH+mWUY5zOsvKaygoDkwNtMp9uhAYs+wRAZ2BysK2qFh8PC70G3BJlJCsMTA52U6kcRbX5X1hHyw7UTLTDY1ExkWYnsesILYDCwKRgRYJm8qjn3G9KkQYsTAq2ddKkY8hkcRrTymoIFBYmBe8wTd2mnnuc3zH00WNiUrBgRRNk1fMB39uXVKCUYeL3TdOMfMZHR5rxnKJk4nK9jXjulmCytRyBCDK/oZs7A12u1ejDgmU9G5PQN5JHHcwzwl0mlEwUnj/4NYqmDlveSVxDwx+ETOjyzkCxOb4lijFgZBLWJzigpCQJH9CMgpjo/G7CH8ZuwlDbo8N8jM/WN0IkwYEDM0wUfvf/3dnMTMKAgjqNalKqBH0z3lRC1VYKmXi83v5jG2FZmBzcsEc3AmKi81rfoytiViaHKlm67mPIhNvJc26VYIK3yfxOgMVKqmiyZeLx+Sd6JtsIy8YkvTTud2G4TcejHCJiwmnmuXdLMdnXL6COSCETBTyd1lo6YXdHqmB9h3rRK2Ziz05sLo2G6dRhZEJstlEfHTPh8ppn7pZlQuoYUAbYlInCY8NA1kszIXTb6JdGt0xk/m6Kgk8dVibh5EF7LVDfJKC+0skysfhb08CyDjOTMMqiL5rZidIx5XIXzoTDUtYYHMEE8cCZsOw/2TJRuPu0oIpPHVomZppwtT6KKohJv5s+q/p+4XJGwsTl7QMs6bUONRMURbJzRAv/YUIjF42UMLF4a9/feMxMMi2k/a8oKt4SJryV9wHQmZmEIfFg5KDqUydMeKtQJplwQsckOvKAo8R5pGAojAlf64HZcELFZJs592z9NJPMWpCXUyY2X/e8uPOYmWBH93dfreGVbUGZnzKx+PorTsaAmUkmIGb2fprZ4qsgoKRM+AqyfjacUDHRAljGq8lHHJN9wukzJnKYwl3VKROFq7tPTUow2QoLHCrWvafeYY4z4amSvT2CSRdzjUQMxT3OhKdG9VQ+igl0FpwKy8byDBOu2gWZi2I2Jv0okGgplCAqWUxKMhgTrvZczO2yTMKouPth8sDUQsehGgRnwlOBMivNJAPD38nCdHtBUyZc9anLM0khxMkYd5lGMzkinsQjYH2S1FkaPXdG5fNOtOK1E08D0pMUTHjqKg3L1yfhxoLcJAlHpRwAy8U83YB4p33CVJ8QE0xmTxc1E67q2M64RP8ksT93WYyeDAKmNXQkvq4BO4Fhl2ZypLD+CWc7/fwlKL8OWBETUPApj9NrCtKbY9XBROfxL0agW7FZdTHRZc66sVsFi2V0h7oTM9FtAKZcxdeM+gt0J8OTMjGAfMfx3vJQwXB6zn4Ph9LSmnJjTHH/k7wEk7wEk7wEk7wEE4L6J1Mzko6QkJCQkJCQkJCQkJCQUFP0f3di6Z8XjVijAAAAAElFTkSuQmCC',
			active: 'false'
		},
		{
			id: '3',
			userName: 'Ali',
			userEmail: 'Ali@i.com',
			image: userImage,
			active: 'true'
		}
	];
	$: filterdUsers = users;

	const filterUsers = (e) => {
		const value = e.detail;
		if (value === 'null') {
			filterdUsers = users;
			return;
		}

		filterdUsers = users.filter((user) => user.active === value);
	};
	//Remove the user
	const remove = ({ detail }) => {
		filterdUsers = filterdUsers.filter((user) => user.id !== detail);
	};
	const addNewUser = ({ detail }) => {
		users = [...users, { id: users.length + 1, ...detail, image: userImage }];
	};
</script>

<section>
	<h1 class="text-2xl text-center mt-10">Users List</h1>
	<!-- Filter Component -->
	<div class="flex justify-between items-center">
		<FilterUser on:filter={filterUsers} />
		<NewUser on:newUser={addNewUser} />
	</div>
	<div>
		{#each filterdUsers as user, i (user.id)}
			<SingleUser on:remove={remove} {i} {user} />
		{:else}
			<p>No Users To Be Shown</p>
		{/each}
	</div>
	<div />
</section>

<style>
</style>

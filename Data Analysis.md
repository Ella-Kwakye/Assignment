ef select_cocoa_bags(bean_count, fat, moisture, fineness, pH, FFA, total_iron, free_iron):
    # Check bean count
    if 80 <= bean_count <= 100:
        cocoa_type = "Main Crop"
        bags_per_pallet = 36
    elif 101 <= bean_count <= 120:
        cocoa_type = "Light Crop"
        bags_per_pallet = 36
    elif 121 <= bean_count <= 130:
        cocoa_type = "Small Beans"
        bags_per_pallet = 36
    else:
        print("Invalid bean count")
        return

    # Check recipe specifications
    if (
        53.3 <= fat <= 53.7
        and moisture <= 1.8
        and fineness <= 0.80
        and 5.2 <= pH <= 6.0
        and FFA <= 2.25
        and total_iron <= 500
        and free_iron <= 150
    ):
        recipe = 1057
    elif (
        52.8 <= fat <= 53.2
        and moisture <= 1.5
        and fineness <= 1.0
        and 5.2 <= pH <= 6.0
        and FFA <= 2.5
        and total_iron <= 350
        and free_iron <= 150
    ):
        recipe = 1030
    else:
        recipe = 1000

    # Calculate the number of bags needed for each cocoa type
    main_crop_bags = 0
    light_crop_bags = 0
    small_beans_bags = 0

    if recipe == 1057:
        main_crop_bags = bean_count // bags_per_pallet * bags_per_pallet
        light_crop_bags = 0
        small_beans_bags = 0
    elif recipe == 1030:
        main_crop_bags = 0
        light_crop_bags = bean_count // bags_per_pallet * bags_per_pallet
        small_beans_bags = 0
    elif recipe == 1000:
        main_crop_bags = 0
        light_crop_bags = 0
        small_beans_bags = bean_count // bags_per_pallet * bags_per_pallet

    print(f"Selected Cocoa Type: {cocoa_type}")
    print(f"Selected Recipe: {recipe}")
    print(f"Main Crop Bags: {main_crop_bags}")
    print(f"Light Crop Bags: {light_crop_bags}")
    print(f"Small Beans Bags: {small_beans_bags}")


# User input
bean_count = int(input("Enter the number of cocoa beans: "))
fat = float(input("Enter fat percentage: "))
moisture = float(input("Enter moisture percentage: "))
fineness = float(input("Enter fineness percentage: "))
pH = float(input("Enter pH value: "))
FFA = float(input("Enter FFA value: "))
total_iron = float(input("Enter total iron in ppm: "))
free_iron = float(input("Enter free iron in ppm: "))

# Call the function
select_cocoa_bags(bean_count, fat, moisture, fineness, pH, FFA, total_iron, free_iron)

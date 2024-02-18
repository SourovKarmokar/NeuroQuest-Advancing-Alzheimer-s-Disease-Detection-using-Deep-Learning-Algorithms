# NeuroQuest-Advancing-Alzheimer-s-Disease-Detection-using-Deep-Learning-Algorithms
Alzheimer's disease is a progressive brain disorder that destroys memory and thinking skills. It's the most common type of dementia.
A search has been initiated within the folder named 'train'.
There are 52 images in the ModerateDemented folder.
There are 717 images in the MildDemented folder.
There are 1792 images in the VeryMildDemented folder.
There are 2573 images in the NonDemented folder.
The search has been completed.

@
class_dist = {}
def image_counter(folder_path):
    basename = os.path.basename(folder_path)
    print('\033[92m'+f"A search has been initiated within the folder named '{basename}'."+'\033[0m')
    image_extensions = ['.jpg', '.jpeg', '.png']https://colab.research.google.com/drive/1OKcDSydW6clnH1JZuR00Wv2Of-nc2co2

    for root, dirs, _ in os.walk(folder_path):
        for dir_name in dirs:
            dir_path = os.path.join(root, dir_name)
            count = 0

            for filename in os.listdir(dir_path):
                file_ext = os.path.splitext(filename)[1].lower()

                if file_ext in image_extensions:
                    count += 1

            class_dist[dir_name] = count
            print(f"There are \033[35m{count}\033[0m images in the {dir_name} folder.")
    print('\033[92m'+"The search has been completed."+'\033[0m')

    keys = list(class_dist.keys())https://github.com/SourovKarmokar/NeuroQuest-Advancing-Alzheimer-s-Disease-Detection-using-Deep-Learning-Algorithms
    values = list(class_dist.values())
    explode = (0.1,)*len(keys)

    labels = [f'{key} ({value} images)' for key, value in zip(keys, values)]

    plt.pie(values, explode=explode,labels=labels, autopct='%1.1f%%',
            shadow=False, startangle=90, colors=colors, textprops={'fontsize': 8 , "color":"black"}, labeldistance=1)
    plt.title("Distribution of \nAlzheimer MRI Images", size=7, fontweight="bold")

PATH = '/content/drive/MyDrive/Alzheimer_data/train'

image_counter(PATH)

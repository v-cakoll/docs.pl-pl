---
title: 'Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach'
description: Dowiedz się, jak tworzyć zdefiniowane przez użytkownika wyjątki przy użyciu zlokalizowanych komunikatów o wyjątkach
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332992"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="1618b-103">Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="1618b-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="1618b-104">W tym artykule przedstawiono sposób tworzenia wyjątków zdefiniowanych przez użytkownika, które są dziedziczone z klasy podstawowej <xref:System.Exception> z zlokalizowanymi komunikatami o wyjątkach przy użyciu zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="1618b-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="1618b-105">Tworzenie wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1618b-105">Create custom exceptions</span></span>

<span data-ttu-id="1618b-106">Platforma .NET zawiera wiele różnych wyjątków, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="1618b-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="1618b-107">Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="1618b-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="1618b-108">Załóżmy, że chcesz utworzyć `StudentNotFoundException`, która zawiera właściwość `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="1618b-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="1618b-109">Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1618b-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="1618b-110">Utwórz klasę z możliwością serializacji, która dziedziczy po <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="1618b-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="1618b-111">Nazwa klasy powinna kończyć się znakiem "Exception":</span><span class="sxs-lookup"><span data-stu-id="1618b-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="1618b-112">Dodaj konstruktory domyślne:</span><span class="sxs-lookup"><span data-stu-id="1618b-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

1. <span data-ttu-id="1618b-113">Zdefiniuj wszelkie dodatkowe właściwości i konstruktory:</span><span class="sxs-lookup"><span data-stu-id="1618b-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="1618b-114">Tworzenie zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="1618b-114">Create localized exception messages</span></span>

<span data-ttu-id="1618b-115">Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1618b-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="1618b-116">Problem z poprzednim wierszem to "nie można znaleźć ucznia".</span><span class="sxs-lookup"><span data-stu-id="1618b-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="1618b-117">jest tylko stałym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="1618b-117">is just a constant string.</span></span> <span data-ttu-id="1618b-118">W zlokalizowanej aplikacji chcesz mieć różne komunikaty w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1618b-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="1618b-119">[Zestawy satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) to dobry sposób na to.</span><span class="sxs-lookup"><span data-stu-id="1618b-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="1618b-120">Zestaw satelicki to plik dll, który zawiera zasoby dla określonego języka.</span><span class="sxs-lookup"><span data-stu-id="1618b-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="1618b-121">Po poproszeniu określonych zasobów w czasie wykonywania środowisko CLR znajdzie ten zasób w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1618b-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="1618b-122">Jeśli nie odnaleziono zestawu satelickiego dla tej kultury, używane są zasoby domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="1618b-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="1618b-123">Aby utworzyć zlokalizowane komunikaty o wyjątkach:</span><span class="sxs-lookup"><span data-stu-id="1618b-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="1618b-124">Utwórz nowy folder o nazwie *resources* , aby przechowywać pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="1618b-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="1618b-125">Dodaj do niego nowy plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="1618b-125">Add a new resource file to it.</span></span> <span data-ttu-id="1618b-126">Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj** -> **nowy element** -> **plik zasobów**.</span><span class="sxs-lookup"><span data-stu-id="1618b-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="1618b-127">Nazwij plik *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="1618b-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="1618b-128">Jest to domyślny plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="1618b-128">This is the default resources file.</span></span>
1. <span data-ttu-id="1618b-129">Dodaj parę nazwa/wartość dla komunikatu o wyjątku, jak pokazano na poniższej ilustracji: @no__t 0Add do domyślnej kultury @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="1618b-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="1618b-130">Dodaj nowy plik zasobów dla języka francuskiego.</span><span class="sxs-lookup"><span data-stu-id="1618b-130">Add a new resource file for French.</span></span> <span data-ttu-id="1618b-131">Nadaj mu nazwę *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="1618b-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="1618b-132">Ponownie Dodaj parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską: @no__t 0Add do kultury fr-FR @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="1618b-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="1618b-133">Po skompilowaniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-fr* z plikiem *dll* , który jest zestawem satelickim.</span><span class="sxs-lookup"><span data-stu-id="1618b-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="1618b-134">Należy zgłosić wyjątek z kodem podobnym do następującego:</span><span class="sxs-lookup"><span data-stu-id="1618b-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="1618b-135">Jeśli nazwa projektu to `TestProject`, a plik zasobów *ExceptionMessages. resx* znajduje się w folderze *resources* projektu, w pełni kwalifikowana nazwa pliku zasobów to `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="1618b-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1618b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1618b-136">See also</span></span>

- [<span data-ttu-id="1618b-137">Jak utworzyć wyjątki zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1618b-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="1618b-138">Tworzenie zestawów satelickich dla aplikacji klasycznych</span><span class="sxs-lookup"><span data-stu-id="1618b-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="1618b-139">Base (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="1618b-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="1618b-140">This (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="1618b-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)

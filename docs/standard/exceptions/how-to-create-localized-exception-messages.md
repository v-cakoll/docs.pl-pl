---
title: 'Instrukcje: tworzenie wyjątków zdefiniowanych przez użytkownika z zastosowaniem zlokalizowanych komunikatów o wyjątkach'
description: Dowiedz się, jak tworzyć zdefiniowane przez użytkownika wyjątki przy użyciu zlokalizowanych komunikatów o wyjątkach
author: Youssef1313
ms.date: 09/13/2019
ms.openlocfilehash: 453e332541628770932da2a6802fdcaee5211a84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141526"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="f0d55-103">Instrukcje: tworzenie wyjątków zdefiniowanych przez użytkownika z zastosowaniem zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="f0d55-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="f0d55-104">W tym artykule opisano sposób tworzenia wyjątków zdefiniowanych przez użytkownika, które są dziedziczone z podstawowej klasy <xref:System.Exception> ze zlokalizowanymi komunikatami o wyjątkach przy użyciu zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="f0d55-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="f0d55-105">Tworzenie wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f0d55-105">Create custom exceptions</span></span>

<span data-ttu-id="f0d55-106">Platforma .NET zawiera wiele różnych wyjątków, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="f0d55-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="f0d55-107">Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="f0d55-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="f0d55-108">Załóżmy, że chcesz utworzyć `StudentNotFoundException`, który zawiera właściwość `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="f0d55-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="f0d55-109">Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f0d55-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="f0d55-110">Utwórz klasę z możliwością serializacji, która dziedziczy po <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="f0d55-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="f0d55-111">Nazwa klasy powinna kończyć się znakiem "Exception":</span><span class="sxs-lookup"><span data-stu-id="f0d55-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="f0d55-112">Dodaj konstruktory domyślne:</span><span class="sxs-lookup"><span data-stu-id="f0d55-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="f0d55-113">Zdefiniuj wszelkie dodatkowe właściwości i konstruktory:</span><span class="sxs-lookup"><span data-stu-id="f0d55-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="f0d55-114">Tworzenie zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="f0d55-114">Create localized exception messages</span></span>

<span data-ttu-id="f0d55-115">Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f0d55-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="f0d55-116">Problem z poprzednim wierszem to, że `"The student cannot be found."` jest tylko stałym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f0d55-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="f0d55-117">W zlokalizowanej aplikacji chcesz mieć różne komunikaty w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f0d55-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="f0d55-118">[Zestawy satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) to dobry sposób na to.</span><span class="sxs-lookup"><span data-stu-id="f0d55-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="f0d55-119">Zestaw satelicki to plik dll, który zawiera zasoby dla określonego języka.</span><span class="sxs-lookup"><span data-stu-id="f0d55-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="f0d55-120">Po poproszeniu określonych zasobów w czasie wykonywania środowisko CLR znajdzie ten zasób w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f0d55-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="f0d55-121">Jeśli nie odnaleziono zestawu satelickiego dla tej kultury, używane są zasoby domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="f0d55-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="f0d55-122">Aby utworzyć zlokalizowane komunikaty o wyjątkach:</span><span class="sxs-lookup"><span data-stu-id="f0d55-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="f0d55-123">Utwórz nowy folder o nazwie *resources* , aby przechowywać pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="f0d55-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="f0d55-124">Dodaj do niego nowy plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="f0d55-124">Add a new resource file to it.</span></span> <span data-ttu-id="f0d55-125">Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksplorator rozwiązań**, a następnie wybierz pozycję **Dodaj** > **nowy element** > **plik zasobów**.</span><span class="sxs-lookup"><span data-stu-id="f0d55-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="f0d55-126">Nazwij plik *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="f0d55-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="f0d55-127">Jest to domyślny plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="f0d55-127">This is the default resources file.</span></span>
1. <span data-ttu-id="f0d55-128">Dodaj parę nazwa/wartość dla komunikatu o wyjątku, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="f0d55-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Dodaj zasoby do domyślnej kultury](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="f0d55-130">Dodaj nowy plik zasobów dla języka francuskiego.</span><span class="sxs-lookup"><span data-stu-id="f0d55-130">Add a new resource file for French.</span></span> <span data-ttu-id="f0d55-131">Nadaj mu nazwę *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="f0d55-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="f0d55-132">Ponownie Dodaj parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską:</span><span class="sxs-lookup"><span data-stu-id="f0d55-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="f0d55-134">Po skompilowaniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-fr* z plikiem *dll* , który jest zestawem satelickim.</span><span class="sxs-lookup"><span data-stu-id="f0d55-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="f0d55-135">Należy zgłosić wyjątek z kodem podobnym do następującego:</span><span class="sxs-lookup"><span data-stu-id="f0d55-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="f0d55-136">Jeśli nazwa projektu jest `TestProject` a plik zasobów *ExceptionMessages. resx* znajduje się w folderze *resources* projektu, w pełni kwalifikowana nazwa pliku zasobów jest `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="f0d55-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0d55-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d55-137">See also</span></span>

- [<span data-ttu-id="f0d55-138">Jak utworzyć wyjątki zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="f0d55-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="f0d55-139">Tworzenie zestawów satelickich dla aplikacji klasycznych</span><span class="sxs-lookup"><span data-stu-id="f0d55-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="f0d55-140">Base (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="f0d55-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="f0d55-141">This (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="f0d55-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)

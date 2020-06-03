---
title: Jak utworzyć wyjątki zdefiniowane przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach
description: Dowiedz się, jak tworzyć zdefiniowane przez użytkownika wyjątki przy użyciu zlokalizowanych komunikatów o wyjątkach
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243352"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="dbe46-103">Jak utworzyć wyjątki zdefiniowane przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="dbe46-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="dbe46-104">W tym artykule opisano sposób tworzenia wyjątków zdefiniowanych przez użytkownika, które są dziedziczone z <xref:System.Exception> klasy podstawowej ze zlokalizowanymi komunikatami o wyjątkach przy użyciu zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="dbe46-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="dbe46-105">Tworzenie wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="dbe46-105">Create custom exceptions</span></span>

<span data-ttu-id="dbe46-106">Platforma .NET zawiera wiele różnych wyjątków, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="dbe46-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="dbe46-107">Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="dbe46-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="dbe46-108">Załóżmy, że chcesz utworzyć element `StudentNotFoundException` , który zawiera `StudentName` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="dbe46-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="dbe46-109">Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="dbe46-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="dbe46-110">Utwórz klasę z możliwością serializacji, która dziedziczy po elemencie <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="dbe46-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="dbe46-111">Nazwa klasy powinna kończyć się znakiem "Exception":</span><span class="sxs-lookup"><span data-stu-id="dbe46-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="dbe46-112">Dodaj konstruktory domyślne:</span><span class="sxs-lookup"><span data-stu-id="dbe46-112">Add the default constructors:</span></span>

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

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="dbe46-113">Zdefiniuj wszelkie dodatkowe właściwości i konstruktory:</span><span class="sxs-lookup"><span data-stu-id="dbe46-113">Define any additional properties and constructors:</span></span>

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

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="dbe46-114">Tworzenie zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="dbe46-114">Create localized exception messages</span></span>

<span data-ttu-id="dbe46-115">Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu przy użyciu kodu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dbe46-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="dbe46-116">Problem z poprzednim wierszem jest `"The student cannot be found."` tylko stałym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="dbe46-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="dbe46-117">W zlokalizowanej aplikacji chcesz mieć różne komunikaty w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dbe46-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="dbe46-118">[Zestawy satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) to dobry sposób na to.</span><span class="sxs-lookup"><span data-stu-id="dbe46-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="dbe46-119">Zestaw satelicki to plik dll, który zawiera zasoby dla określonego języka.</span><span class="sxs-lookup"><span data-stu-id="dbe46-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="dbe46-120">Po poproszeniu określonych zasobów w czasie wykonywania środowisko CLR znajdzie ten zasób w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dbe46-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="dbe46-121">Jeśli nie odnaleziono zestawu satelickiego dla tej kultury, używane są zasoby domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="dbe46-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="dbe46-122">Aby utworzyć zlokalizowane komunikaty o wyjątkach:</span><span class="sxs-lookup"><span data-stu-id="dbe46-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="dbe46-123">Utwórz nowy folder o nazwie *resources* , aby przechowywać pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="dbe46-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="dbe46-124">Dodaj do niego nowy plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="dbe46-124">Add a new resource file to it.</span></span> <span data-ttu-id="dbe46-125">Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**  >  **nowy element**  >  **zasobów**elementu.</span><span class="sxs-lookup"><span data-stu-id="dbe46-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="dbe46-126">Nazwij plik *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="dbe46-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="dbe46-127">Jest to domyślny plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="dbe46-127">This is the default resources file.</span></span>
1. <span data-ttu-id="dbe46-128">Dodaj parę nazwa/wartość dla komunikatu o wyjątku, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="dbe46-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Dodaj zasoby do domyślnej kultury](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="dbe46-130">Dodaj nowy plik zasobów dla języka francuskiego.</span><span class="sxs-lookup"><span data-stu-id="dbe46-130">Add a new resource file for French.</span></span> <span data-ttu-id="dbe46-131">Nadaj mu nazwę *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="dbe46-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="dbe46-132">Ponownie Dodaj parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską:</span><span class="sxs-lookup"><span data-stu-id="dbe46-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="dbe46-134">Po skompilowaniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-fr* z plikiem *dll* , który jest zestawem satelickim.</span><span class="sxs-lookup"><span data-stu-id="dbe46-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="dbe46-135">Należy zgłosić wyjątek z kodem podobnym do następującego:</span><span class="sxs-lookup"><span data-stu-id="dbe46-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="dbe46-136">Jeśli nazwa projektu to, `TestProject` a plik zasobów *ExceptionMessages. resx* znajduje się w folderze *resources* projektu, w pełni kwalifikowana nazwa pliku zasobów to `TestProject.Resources.ExceptionMessages` .</span><span class="sxs-lookup"><span data-stu-id="dbe46-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbe46-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbe46-137">See also</span></span>

- [<span data-ttu-id="dbe46-138">Jak utworzyć wyjątki zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="dbe46-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="dbe46-139">Tworzenie zestawów satelickich dla aplikacji klasycznych</span><span class="sxs-lookup"><span data-stu-id="dbe46-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="dbe46-140">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dbe46-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="dbe46-141">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dbe46-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)

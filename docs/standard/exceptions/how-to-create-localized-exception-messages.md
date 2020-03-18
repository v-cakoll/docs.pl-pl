---
title: Jak tworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanych komunikatów o wyjątkach
description: Dowiedz się, jak tworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanych komunikatów o wyjątkach
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160186"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="c5179-103">Jak tworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="c5179-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="c5179-104">W tym artykule dowiesz się, jak utworzyć wyjątki zdefiniowane przez <xref:System.Exception> użytkownika, które są dziedziczone z klasy podstawowej z zlokalizowanych komunikatów wyjątków przy użyciu zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="c5179-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="c5179-105">Tworzenie wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c5179-105">Create custom exceptions</span></span>

<span data-ttu-id="c5179-106">.NET zawiera wiele różnych wyjątków, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="c5179-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="c5179-107">Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia twoich potrzeb, można utworzyć własne wyjątki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="c5179-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="c5179-108">Załóżmy, że chcesz `StudentNotFoundException` utworzyć właściwość `StudentName` zawierającą właściwość.</span><span class="sxs-lookup"><span data-stu-id="c5179-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="c5179-109">Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c5179-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="c5179-110">Utwórz klasę serializable, <xref:System.Exception>która dziedziczy z .</span><span class="sxs-lookup"><span data-stu-id="c5179-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="c5179-111">Nazwa klasy powinna kończyć się na "Wyjątek":</span><span class="sxs-lookup"><span data-stu-id="c5179-111">The class name should end in "Exception":</span></span>

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

1. <span data-ttu-id="c5179-112">Dodaj domyślne konstruktory:</span><span class="sxs-lookup"><span data-stu-id="c5179-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="c5179-113">Zdefiniuj dodatkowe właściwości i konstruktory:</span><span class="sxs-lookup"><span data-stu-id="c5179-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="c5179-114">Tworzenie zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="c5179-114">Create localized exception messages</span></span>

<span data-ttu-id="c5179-115">Utworzyłeś wyjątek niestandardowy i możesz go zgłosić w dowolnym miejscu za pomocą kodu, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="c5179-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="c5179-116">Problem z poprzednim wierszem `"The student cannot be found."` jest to, że jest tylko stały ciąg.</span><span class="sxs-lookup"><span data-stu-id="c5179-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="c5179-117">W zlokalizowanej aplikacji chcesz mieć różne wiadomości w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5179-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="c5179-118">[Zespoły satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) są dobrym sposobem, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c5179-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="c5179-119">Zestaw satelitarny jest .dll, który zawiera zasoby dla określonego języka.</span><span class="sxs-lookup"><span data-stu-id="c5179-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="c5179-120">Gdy poprosisz o określonych zasobów w czasie wykonywania, CLR znajdzie tego zasobu w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5179-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="c5179-121">Jeśli nie zostanie znaleziony zestaw satelicki dla tej kultury, używane są zasoby kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c5179-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="c5179-122">Aby utworzyć zlokalizowane komunikaty o wyjątkach:</span><span class="sxs-lookup"><span data-stu-id="c5179-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="c5179-123">Utwórz nowy folder o nazwie *Zasoby* do przechowywania plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="c5179-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="c5179-124">Dodaj do niego nowy plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="c5179-124">Add a new resource file to it.</span></span> <span data-ttu-id="c5179-125">Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksploratorze rozwiązań**i wybierz polecenie **Dodaj** > nowy**plik zasobów\*\*\*\*elementu** > .</span><span class="sxs-lookup"><span data-stu-id="c5179-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="c5179-126">Nazwij plik *ExceptionMessages.resx*.</span><span class="sxs-lookup"><span data-stu-id="c5179-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="c5179-127">Jest to domyślny plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="c5179-127">This is the default resources file.</span></span>
1. <span data-ttu-id="c5179-128">Dodaj parę nazw i wartości dla komunikatu o wyjątku, na przykład na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="c5179-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Dodawanie zasobów do kultury domyślnej](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="c5179-130">Dodaj nowy plik zasobów dla języka francuskiego.</span><span class="sxs-lookup"><span data-stu-id="c5179-130">Add a new resource file for French.</span></span> <span data-ttu-id="c5179-131">Nazwij go *ExceptionMessages.fr-FR.resx*.</span><span class="sxs-lookup"><span data-stu-id="c5179-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="c5179-132">Dodaj ponownie parę nazw/wartości dla komunikatu o wyjątku, ale z wartością francuską:</span><span class="sxs-lookup"><span data-stu-id="c5179-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="c5179-134">Po utworzenia projektu folder wyjściowy kompilacji powinien zawierać folder *fr-FR* z plikiem *dll,* który jest zestawem sateczkowym.</span><span class="sxs-lookup"><span data-stu-id="c5179-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="c5179-135">Zgłaszasz wyjątek z kodem, takim jak następujące:</span><span class="sxs-lookup"><span data-stu-id="c5179-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="c5179-136">Jeśli nazwa projektu `TestProject` jest i plik zasobów *ExceptionMessages.resx* znajduje się w folderze *Zasoby* projektu, `TestProject.Resources.ExceptionMessages`w pełni kwalifikowaną nazwą pliku zasobu jest .</span><span class="sxs-lookup"><span data-stu-id="c5179-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5179-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5179-137">See also</span></span>

- [<span data-ttu-id="c5179-138">Jak utworzyć wyjątki zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c5179-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="c5179-139">Tworzenie zestawów satelickich dla aplikacji klasycznych</span><span class="sxs-lookup"><span data-stu-id="c5179-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="c5179-140">base (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5179-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="c5179-141">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5179-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)

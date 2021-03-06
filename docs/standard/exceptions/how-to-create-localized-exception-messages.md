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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Jak utworzyć wyjątki zdefiniowane przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach

W tym artykule opisano sposób tworzenia wyjątków zdefiniowanych przez użytkownika, które są dziedziczone z <xref:System.Exception> klasy podstawowej ze zlokalizowanymi komunikatami o wyjątkach przy użyciu zestawów satelickich.

## <a name="create-custom-exceptions"></a>Tworzenie wyjątków niestandardowych

Platforma .NET zawiera wiele różnych wyjątków, których można użyć. Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.

Załóżmy, że chcesz utworzyć element `StudentNotFoundException` , który zawiera `StudentName` Właściwość.
Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:

1. Utwórz klasę z możliwością serializacji, która dziedziczy po elemencie <xref:System.Exception> . Nazwa klasy powinna kończyć się znakiem "Exception":

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

1. Dodaj konstruktory domyślne:

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

1. Zdefiniuj wszelkie dodatkowe właściwości i konstruktory:

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

## <a name="create-localized-exception-messages"></a>Tworzenie zlokalizowanych komunikatów o wyjątkach

Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu przy użyciu kodu w następujący sposób:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Problem z poprzednim wierszem jest `"The student cannot be found."` tylko stałym ciągiem. W zlokalizowanej aplikacji chcesz mieć różne komunikaty w zależności od kultury użytkownika.
[Zestawy satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) to dobry sposób na to. Zestaw satelicki to plik dll, który zawiera zasoby dla określonego języka. Po poproszeniu określonych zasobów w czasie wykonywania środowisko CLR znajdzie ten zasób w zależności od kultury użytkownika. Jeśli nie odnaleziono zestawu satelickiego dla tej kultury, używane są zasoby domyślnej kultury.

Aby utworzyć zlokalizowane komunikaty o wyjątkach:

1. Utwórz nowy folder o nazwie *resources* , aby przechowywać pliki zasobów.
1. Dodaj do niego nowy plik zasobów. Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj**  >  **nowy element**  >  **zasobów**elementu. Nazwij plik *ExceptionMessages. resx*. Jest to domyślny plik zasobów.
1. Dodaj parę nazwa/wartość dla komunikatu o wyjątku, jak pokazano na poniższej ilustracji:

   ![Dodaj zasoby do domyślnej kultury](media/add-resources-to-default-culture.jpg)

1. Dodaj nowy plik zasobów dla języka francuskiego. Nadaj mu nazwę *ExceptionMessages.fr-fr. resx*.
1. Ponownie Dodaj parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską:

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. Po skompilowaniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-fr* z plikiem *dll* , który jest zestawem satelickim.
1. Należy zgłosić wyjątek z kodem podobnym do następującego:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Jeśli nazwa projektu to, `TestProject` a plik zasobów *ExceptionMessages. resx* znajduje się w folderze *resources* projektu, w pełni kwalifikowana nazwa pliku zasobów to `TestProject.Resources.ExceptionMessages` .

## <a name="see-also"></a>Zobacz też

- [Jak utworzyć wyjątki zdefiniowane przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Tworzenie zestawów satelickich dla aplikacji klasycznych](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (odwołanie w C#)](../../csharp/language-reference/keywords/base.md)
- [this (odwołanie w C#)](../../csharp/language-reference/keywords/this.md)

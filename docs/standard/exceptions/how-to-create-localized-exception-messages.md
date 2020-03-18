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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Jak tworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanych komunikatów o wyjątkach

W tym artykule dowiesz się, jak utworzyć wyjątki zdefiniowane przez <xref:System.Exception> użytkownika, które są dziedziczone z klasy podstawowej z zlokalizowanych komunikatów wyjątków przy użyciu zestawów satelickich.

## <a name="create-custom-exceptions"></a>Tworzenie wyjątków niestandardowych

.NET zawiera wiele różnych wyjątków, których można użyć. Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia twoich potrzeb, można utworzyć własne wyjątki niestandardowe.

Załóżmy, że chcesz `StudentNotFoundException` utworzyć właściwość `StudentName` zawierającą właściwość.
Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:

1. Utwórz klasę serializable, <xref:System.Exception>która dziedziczy z . Nazwa klasy powinna kończyć się na "Wyjątek":

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

1. Dodaj domyślne konstruktory:

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

1. Zdefiniuj dodatkowe właściwości i konstruktory:

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

Utworzyłeś wyjątek niestandardowy i możesz go zgłosić w dowolnym miejscu za pomocą kodu, takiego jak:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Problem z poprzednim wierszem `"The student cannot be found."` jest to, że jest tylko stały ciąg. W zlokalizowanej aplikacji chcesz mieć różne wiadomości w zależności od kultury użytkownika.
[Zespoły satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) są dobrym sposobem, aby to zrobić. Zestaw satelitarny jest .dll, który zawiera zasoby dla określonego języka. Gdy poprosisz o określonych zasobów w czasie wykonywania, CLR znajdzie tego zasobu w zależności od kultury użytkownika. Jeśli nie zostanie znaleziony zestaw satelicki dla tej kultury, używane są zasoby kultury domyślnej.

Aby utworzyć zlokalizowane komunikaty o wyjątkach:

1. Utwórz nowy folder o nazwie *Zasoby* do przechowywania plików zasobów.
1. Dodaj do niego nowy plik zasobu. Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksploratorze rozwiązań**i wybierz polecenie **Dodaj** > nowy**plik zasobów****elementu** > . Nazwij plik *ExceptionMessages.resx*. Jest to domyślny plik zasobów.
1. Dodaj parę nazw i wartości dla komunikatu o wyjątku, na przykład na poniższej ilustracji:

   ![Dodawanie zasobów do kultury domyślnej](media/add-resources-to-default-culture.jpg)

1. Dodaj nowy plik zasobów dla języka francuskiego. Nazwij go *ExceptionMessages.fr-FR.resx*.
1. Dodaj ponownie parę nazw/wartości dla komunikatu o wyjątku, ale z wartością francuską:

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. Po utworzenia projektu folder wyjściowy kompilacji powinien zawierać folder *fr-FR* z plikiem *dll,* który jest zestawem sateczkowym.
1. Zgłaszasz wyjątek z kodem, takim jak następujące:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Jeśli nazwa projektu `TestProject` jest i plik zasobów *ExceptionMessages.resx* znajduje się w folderze *Zasoby* projektu, `TestProject.Resources.ExceptionMessages`w pełni kwalifikowaną nazwą pliku zasobu jest .

## <a name="see-also"></a>Zobacz też

- [Jak utworzyć wyjątki zdefiniowane przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Tworzenie zestawów satelickich dla aplikacji klasycznych](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (odwołanie w C#)](../../csharp/language-reference/keywords/base.md)
- [this (odwołanie w C#)](../../csharp/language-reference/keywords/this.md)

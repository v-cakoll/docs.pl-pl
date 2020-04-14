---
title: Jak utworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanymi komunikatami o wyjątkach
description: Dowiedz się, jak tworzyć wyjątki zdefiniowane przez użytkownika za pomocą zlokalizowanych komunikatów o wyjątkach
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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Jak utworzyć wyjątki zdefiniowane przez użytkownika z zlokalizowanymi komunikatami o wyjątkach

W tym artykule dowiesz się, jak utworzyć wyjątki zdefiniowane <xref:System.Exception> przez użytkownika, które są dziedziczone z klasy podstawowej z zlokalizowanych komunikatów wyjątków przy użyciu zestawów satelitarnych.

## <a name="create-custom-exceptions"></a>Tworzenie wyjątków niestandardowych

.NET zawiera wiele różnych wyjątków, których można użyć. Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.

Załóżmy, `StudentNotFoundException` że chcesz utworzyć, `StudentName` który zawiera właściwość.
Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:

1. Utwórz klasę serializowalną, która dziedziczy po <xref:System.Exception>pliku . Nazwa klasy powinna kończyć się na "Wyjątek":

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

Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu z kodem, jak poniżej:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Problem z poprzednim wierszem `"The student cannot be found."` jest to, że jest tylko stały ciąg. W zlokalizowane aplikacji, które mają mieć różne komunikaty w zależności od kultury użytkownika.
[Zestawy satelitarne](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) są dobrym sposobem, aby to zrobić. Zestaw satelicki to biblioteka dll zawierająca zasoby dla określonego języka. Gdy poprosisz o określone zasoby w czasie wykonywania, środowisko CLR wyszukuje ten zasób w zależności od kultury użytkownika. Jeśli nie znaleziono zestawu satelickiego dla tej kultury, zasoby kultury domyślnej są używane.

Aby utworzyć zlokalizowane komunikaty wyjątków:

1. Utwórz nowy folder o nazwie *Zasoby* do przechowywania plików zasobów.
1. Dodaj do niego nowy plik zasobów. Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksploratorze rozwiązań**i wybierz polecenie **Dodaj** > **nowy plik zasobów****elementów** > . Nazwij plik *ExceptionMessages.resx*. Jest to domyślny plik zasobów.
1. Dodaj parę nazwa/wartość dla wiadomości o wyjątku, na przykład na poniższej ilustracji:

   ![Dodawanie zasobów do kultury domyślnej](media/add-resources-to-default-culture.jpg)

1. Dodaj nowy plik zasobów dla języka francuskiego. Nazwij go *ExceptionMessages.fr-FR.resx*.
1. Dodaj ponownie parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską:

   ![Dodawanie zasobów do kultury fr-FR](media/add-resources-to-fr-culture.jpg)

1. Po utworzeniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-FR* z plikiem *.dll,* który jest zestawem satelickiego.
1. Zgłaszasz wyjątek z kodem następującym:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Jeśli nazwa projektu `TestProject` jest i plik zasobów *ExceptionMessages.resx* znajduje się w folderze *Zasoby* projektu, `TestProject.Resources.ExceptionMessages`w pełni kwalifikowana nazwa pliku zasobu jest .

## <a name="see-also"></a>Zobacz też

- [Jak utworzyć wyjątki zdefiniowane przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Tworzenie zestawów satelickich dla aplikacji klasycznych](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (odwołanie w C#)](../../csharp/language-reference/keywords/base.md)
- [this (odwołanie w C#)](../../csharp/language-reference/keywords/this.md)

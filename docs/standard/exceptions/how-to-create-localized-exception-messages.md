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
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach

W tym artykule przedstawiono sposób tworzenia wyjątków zdefiniowanych przez użytkownika, które są dziedziczone z klasy podstawowej <xref:System.Exception> z zlokalizowanymi komunikatami o wyjątkach przy użyciu zestawów satelickich.

## <a name="create-custom-exceptions"></a>Tworzenie wyjątków niestandardowych

Platforma .NET zawiera wiele różnych wyjątków, których można użyć. Jednak w niektórych przypadkach, gdy żaden z nich nie spełnia Twoich potrzeb, można utworzyć własne wyjątki niestandardowe.

Załóżmy, że chcesz utworzyć `StudentNotFoundException`, która zawiera właściwość `StudentName`.
Aby utworzyć wyjątek niestandardowy, wykonaj następujące kroki:

1. Utwórz klasę z możliwością serializacji, która dziedziczy po <xref:System.Exception>. Nazwa klasy powinna kończyć się znakiem "Exception":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
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

## <a name="create-localized-exception-messages"></a>Tworzenie zlokalizowanych komunikatów o wyjątkach

Utworzono wyjątek niestandardowy i można go zgłosić w dowolnym miejscu przy użyciu kodu w następujący sposób:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

Problem z poprzednim wierszem to "nie można znaleźć ucznia". jest tylko stałym ciągiem. W zlokalizowanej aplikacji chcesz mieć różne komunikaty w zależności od kultury użytkownika.
[Zestawy satelickie](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) to dobry sposób na to. Zestaw satelicki to plik dll, który zawiera zasoby dla określonego języka. Po poproszeniu określonych zasobów w czasie wykonywania środowisko CLR znajdzie ten zasób w zależności od kultury użytkownika. Jeśli nie odnaleziono zestawu satelickiego dla tej kultury, używane są zasoby domyślnej kultury.

Aby utworzyć zlokalizowane komunikaty o wyjątkach:

1. Utwórz nowy folder o nazwie *resources* , aby przechowywać pliki zasobów.
1. Dodaj do niego nowy plik zasobów. Aby to zrobić w programie Visual Studio, kliknij prawym przyciskiem myszy folder w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj** -> **nowy element** -> **plik zasobów**. Nazwij plik *ExceptionMessages. resx*. Jest to domyślny plik zasobów.
1. Dodaj parę nazwa/wartość dla komunikatu o wyjątku, jak pokazano na poniższej ilustracji: @no__t 0Add do domyślnej kultury @ no__t-1
1. Dodaj nowy plik zasobów dla języka francuskiego. Nadaj mu nazwę *ExceptionMessages.fr-fr. resx*.
1. Ponownie Dodaj parę nazwa/wartość dla komunikatu o wyjątku, ale z wartością francuską: @no__t 0Add do kultury fr-FR @ no__t-1
1. Po skompilowaniu projektu folder wyjściowy kompilacji powinien zawierać folder *fr-fr* z plikiem *dll* , który jest zestawem satelickim.
1. Należy zgłosić wyjątek z kodem podobnym do następującego:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > Jeśli nazwa projektu to `TestProject`, a plik zasobów *ExceptionMessages. resx* znajduje się w folderze *resources* projektu, w pełni kwalifikowana nazwa pliku zasobów to `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Zobacz także

- [Jak utworzyć wyjątki zdefiniowane przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Tworzenie zestawów satelickich dla aplikacji klasycznych](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Base (C# odwołanie)](../../csharp/language-reference/keywords/base.md)
- [This (C# odwołanie)](../../csharp/language-reference/keywords/this.md)

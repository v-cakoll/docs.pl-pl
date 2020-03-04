---
title: 'Przewodnik: utrwalanie obiektu za pomocąC#'
ms.date: 04/26/2018
ms.openlocfilehash: 9531909bdf1ed61305c292411ef2cd08b7b67465
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240470"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Przewodnik: utrwalanie obiektu przy użyciu języka C\#

Możesz użyć serializacji, aby zachować dane obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym utworzeniu wystąpienia obiektu.

W tym instruktażu utworzysz podstawowy obiekt `Loan` i zachowasz jego dane do pliku. Następnie dane zostaną pobrane z pliku po ponownym utworzeniu obiektu.

> [!IMPORTANT]
> Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć uprawnienie `Create` do tego folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` uprawnienia, ale jest to małe uprawnienie. Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie uprawnień `Read` tylko do jednego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder Program Files.

> [!IMPORTANT]
> Ten przykład zapisuje dane w pliku formatu binarnego. Tych formatów nie należy używać w przypadku poufnych danych, takich jak hasła lub informacje o kartach kredytowych.

## <a name="prerequisites"></a>Wymagania wstępne

- Aby skompilować i uruchomić, zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).

- Zainstaluj swój ulubiony Edytor kodu, jeśli jeszcze tego nie zrobiono.

> [!TIP]
> Musisz zainstalować Edytor kodu? Wypróbuj [program Visual Studio](https://visualstudio.com/downloads)!

- Przykład wymaga C# 7,3. Zobacz [Wybieranie wersji C# językowej](../../../language-reference/configure-language-version.md) 

Przykładowy kod można przeanalizować w trybie online [w repozytorium usługi GitHub dla platformy .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczek

Pierwszym krokiem jest utworzenie klasy `Loan` i aplikacji konsolowej, która używa klasy:

1. Utwórz nową aplikację. Wpisz `dotnet new console -o serialization`, aby utworzyć nową aplikację konsolową w podkatalogu o nazwie `serialization`.
1. Otwórz aplikację w edytorze i Dodaj nową klasę o nazwie `Loan.cs`.
1. Dodaj następujący kod do klasy `Loan`:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Należy również utworzyć aplikację, która używa klasy `Loan`.

## <a name="serialize-the-loan-object"></a>Serializacja obiektu pożyczek

1. Otwórz plik `Program.cs`. Dodaj następujący kod:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Dodaj program obsługi zdarzeń dla zdarzenia `PropertyChanged` i kilka wierszy, aby zmodyfikować obiekt `Loan` i wyświetlić zmiany. Można zobaczyć dodatki w następującym kodzie:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

W tym momencie można uruchomić kod i wyświetlić bieżące dane wyjściowe:

```console
New customer value: Henry Clay
7.5
7.1
```

Aplikacja wielokrotnie uruchamiana zawsze zapisuje te same wartości. Nowy obiekt pożyczek jest tworzony za każdym razem, gdy uruchamiasz program. W świecie rzeczywistym stawki odsetek zmieniają się okresowo, ale nie zawsze, gdy aplikacja jest uruchomiona. Kod serializacji oznacza zachowywanie najnowszej stopy odsetek między wystąpieniami aplikacji. W następnym kroku wystarczy dodać serializację do klasy pożyczek.

## <a name="using-serialization-to-persist-the-object"></a>Utrwalanie obiektu przy użyciu serializacji

Aby zachować wartości dla klasy pożyczek, należy najpierw oznaczyć klasę atrybutem `Serializable`. Dodaj następujący kod powyżej definicji klasy pożyczek:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> informuje kompilator, że wszystko w klasie może być utrwalone w pliku. Ponieważ zdarzenie `PropertyChanged` nie reprezentuje części grafu obiektów, która powinna być przechowywana, nie powinno być serializowane. Dzięki temu można serializować wszystkie obiekty, które są dołączone do tego zdarzenia. Można dodać <xref:System.NonSerializedAttribute> do deklaracji pola dla programu obsługi zdarzeń `PropertyChanged`.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

Począwszy od C# 7,3, można dołączyć atrybuty do pola zapasowego właściwości automatycznie zaimplementowane przy użyciu wartości docelowej `field`. Poniższy kod dodaje właściwość `TimeLastLoaded` i oznacza ją jako niemożliwy do serializacji:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp. Aby serializować klasę i zapisać ją w pliku, należy użyć przestrzeni nazw <xref:System.IO> i <xref:System.Runtime.Serialization.Formatters.Binary>. Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych przestrzeni nazw, jak pokazano w poniższym kodzie:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Następnym krokiem jest dodanie kodu w celu deserializacji obiektu z pliku po utworzeniu obiektu. Dodaj stałą do klasy dla nazwy pliku serializowanej danych, jak pokazano w poniższym kodzie:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Następnie Dodaj następujący kod po wierszu, który tworzy obiekt `TestLoan`:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Najpierw należy sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz klasę <xref:System.IO.Stream>, aby odczytać plik binarny i klasę <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, aby przetłumaczyć plik. Należy również przekonwertować typ strumienia na typ obiektu pożyczki.

Następnie musisz dodać kod, aby serializować klasę do pliku. Dodaj następujący kod po istniejącym kodzie w metodzie `Main`:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

W tym momencie możesz ponownie skompilować i uruchomić aplikację. Przy pierwszym uruchomieniu należy zauważyć, że stawki odsetek zaczynają się od 7,5, a następnie zmieniają się na 7,1. Zamknij aplikację, a następnie uruchom ją ponownie. Teraz aplikacja drukuje wiadomość, która odczytała zapisany plik, a oprocentowanie to 7,1 nawet przed kodem, który go zmieni.

## <a name="see-also"></a>Zobacz też

- [Serializacja (C#)](index.md)
- [Przewodnik programowania w języku C#](../..//index.md)

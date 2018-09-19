---
title: 'Przewodnik: Przechowywanie obiektu przy użyciu języka C#'
ms.date: 04/26/2018
ms.openlocfilehash: c3cff57f008eb524c2d2bec406431e4c41dca617
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45999419"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Przewodnik: przechowywanie obiektu przy użyciu języka C# #

Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, dzięki czemu możesz przechowywać wartości, a następnie pobrać jednego z nich przy następnym uruchomieniu jest tworzone wystąpienie obiektu.

W tym instruktażu utworzysz podstawową `Loan` obiekt i utrwala jego dane do pliku. Następnie powoduje pobranie danych z pliku, gdy ponownie utworzyć obiekt.

> [!IMPORTANT]
> Ten przykład tworzy nowy plik, jeśli go jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć `Create` uprawnienie do tego folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` uprawnienia, mniejsze uprawnienia. Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub do folderu Program Files.

> [!IMPORTANT]
> W tym przykładzie przechowuje dane w pliku binarnym. Nie można używać tych formatów poufnych danych, takie jak hasła lub informacji o karcie kredytowej.

## <a name="prerequisites"></a>Wymagania wstępne

* Aby skompilować i uruchomić, należy zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/core).

* Wybrany edytor kodu, należy zainstalować, jeśli jeszcze go.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!

Kod przykładowy w trybie online, można sprawdzić [w repozytorium GitHub samples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki

Pierwszym krokiem jest utworzenie `Loan` klasy i aplikację konsolową, która używa klasy:

1. Utwórz nową aplikację. Typ `dotnet new console -o serialization` utworzyć nową aplikację konsolową w podkatalogu o nazwie `serialization`.
1. Otwórz aplikację w edytorze i Dodaj nową klasę o nazwie `Loan.cs`.
1. Dodaj następujący kod, aby Twoje `Loan` klasy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Należy również utworzyć aplikację, która używa `Loan` klasy.

## <a name="serialize-the-loan-object"></a>Serializacji obiektu pożyczki

1. Otwórz `Program.cs`. Dodaj następujący kod:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

Dodawanie obsługi zdarzeń dla `PropertyChanged` zdarzeń i kilka wierszy, aby zmodyfikować `Loan` obiektów i wyświetlić zmiany. Możesz zobaczyć dodatki w poniższym kodzie:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

W tym momencie możesz uruchomić kod i wyświetlone bieżące dane wyjściowe:

```console
New customer value: Henry Clay
7.5
7.1
```

Uruchomienie takiej aplikacji wielokrotnie zawsze zapisuje te same wartości. Za każdym razem, gdy program zostanie uruchomiony, tworzony jest nowy obiekt pożyczki. W świecie rzeczywistym oprocentowania zmienić okresowo, ale niekoniecznie każdorazowym uruchomieniu aplikacji. Kod serializacji oznacza, że Zachowaj najnowsze stopie między wystąpieniami aplikacji. W następnym kroku będziesz robić to dodając serializacji do klasy pożyczki.

## <a name="using-serialization-to-persist-the-object"></a>Za pomocą serializacji, aby utrwalić obiektu

Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę za pomocą `Serializable` atrybutu. Dodaj następujący kod nad pożyczki definicji klasy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Informuje kompilator, że wszystkie elementy w klasie mogą zostać utrwalone w pliku. Ponieważ `PropertyChanged` zdarzenia nie reprezentuje część wykresu obiektu, który ma być przechowywany, nie powinien podlegać serializacji. Ten sposób może serializować wszystkie obiekty, które są dołączone do tego zdarzenia. Możesz dodać <xref:System.NonSerializedAttribute> na deklarację pola dla `PropertyChanged` programu obsługi zdarzeń.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

Począwszy od języka C# 7.3, można dołączyć atrybutów do usługi przy użyciu automatycznie implementowanych właściwości pola zapasowego `field` wartość docelowa. Poniższy kod dodaje `TimeLastLoaded` właściwości i oznacza je jako nelze serializovat.:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Następnym krokiem jest dodać kod serializacji do aplikacji LoanApp. Aby można było serializować klasy i zapisze go w pliku, użyj <xref:System.IO> i <xref:System.Runtime.Serialization.Formatters.Binary> przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do przestrzeni nazw wymaganych, jak pokazano w poniższym kodzie:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Następnym krokiem jest dodawanie kodu do deserializacji obiektu na podstawie pliku, gdy obiekt zostanie utworzony. Dodaj stałą do klasy dla nazwy pliku serializowane dane, jak pokazano w poniższym kodzie:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

Następnie dodaj następujący kod po wierszu, który tworzy `TestLoan` obiektu:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

Najpierw musisz sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy można odczytać pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku. Należy również konwersji z typu strumienia do typu obiektu pożyczki.

Następnie należy dodać kod do serializacji klas w pliku. Dodaj następujący kod po istniejący kod w `Main` metody:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

W tym momencie możesz ponownie skompiluj i uruchom aplikację. Przy pierwszym uruchomieniu, należy zauważyć, że odsetek rozpoczyna się w wersji 7.5, a następnie zmienia 7.1. Zamknij aplikację, a następnie uruchom ją ponownie. Teraz aplikacja wyświetla komunikat, że ma ona odczytu zapisany plik, a stopę 7.1, nawet przed kod, który zmienia ją.

## <a name="see-also"></a>Zobacz też

- [Serializacja (C#)](index.md)  
- [Przewodnik programowania w języku C#](../..//index.md)  

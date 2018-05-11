---
title: 'Wskazówki: Przechowywanie obiektu przy użyciu języka C#'
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Wskazówki: przechowywanie obiektu przy użyciu języka C# #

Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, które umożliwia przechowywanie wartości i pobrać je przy następnym uruchomieniu tworzenia wystąpienia obiektu klasy.

W tym przewodniku spowoduje utworzenie podstawowego `Loan` obiekt i utrwala jego danych do pliku. Następnie zostanie pobrać dane z pliku podczas ponownego tworzenia obiektu.

> [!IMPORTANT]
> W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, musi mieć aplikację `Create` uprawnienia do tego folderu. Uprawnienia są skonfigurowane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi tylko `Write` uprawnienia, mniejszym uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.

> [!IMPORTANT]
> W tym przykładzie przechowuje dane w pliku binarnym. Nie można używać tych formatów dla poufnych danych, takie jak hasła lub karty kredytowej.

## <a name="prerequisites"></a>Wymagania wstępne

* Aby skompilować i uruchomić, należy zainstalować [.NET Core SDK](https://www.microsoft.com/net/core).

* Jeśli nie jest jeszcze, należy zainstalować w edytorze kodu ulubionych.

> [!TIP]
> Należy zainstalować Edytor kodu? Spróbuj [programu Visual Studio](https://visualstudio.com/downloads)!

Można sprawdzić w trybie online przykładowym kodzie [w repozytorium GitHub przykłady .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki

Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja konsolowa, która używa klasy:

1. Utwórz nową aplikację. Typ `dotnet new console -o serialization` Aby utworzyć nową aplikację konsoli w podkatalogu o nazwie `serialization`.
1. Otwórz aplikację w edytorze i Dodaj nową klasę o nazwie `Loan.cs`.
1. Dodaj następujący kod do Twojej `Loan` klasy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

Należy także utworzyć aplikację, która używa `Loan` klasy.

## <a name="serialize-the-loan-object"></a>Serializacji obiektu pożyczki

1. Otwórz `Program.cs`. Dodaj następujący kod:

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzeń i kilka wierszy do modyfikowania `Loan` obiektu i wyświetlić zmiany. Można wyświetlić dodatków w następującym kodzie:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

W tym momencie możesz uruchomić kod i wyświetlone bieżące dane wyjściowe:

```console
New customer value: Henry Clay
7.5
7.1
```

Uruchomienie takiej aplikacji wielokrotnie zawsze zapisuje te same wartości. Za każdym razem, gdy program zostanie uruchomiony, jest tworzony nowy obiekt pożyczki. W świecie rzeczywistym odsetek zmienić okresowo, ale niekoniecznie każdym uruchomieniu aplikacji. Kod serializacji oznacza, że Zachowaj najnowsze stopie procentowej między wystąpieniami aplikacji. W następnym kroku zostanie czy właśnie tę dodając serializacji do klasy pożyczki.

## <a name="using-serialization-to-persist-the-object"></a>Za pomocą serializacji, aby utrwalić obiektu

Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę atrybutem `Serializable` atrybutu. Dodaj następujący kod nad pożyczki definicji klasy:

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> Informuje kompilator, że wszystkie elementy w klasie mógł być trwały do pliku. Ponieważ `PropertyChanged` zdarzenia nie reprezentuje część wykres obiektu, który powinien być przechowywany, nie powinien podlegać serializacji. Dzięki temu będzie serializować wszystkie obiekty, które są dołączone do tego zdarzenia. Możesz dodać <xref:System.NonSerializedAttribute> do zgłoszenia pola `PropertyChanged` obsługi zdarzeń.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

Począwszy od 7.3 C#, możesz dołączyć atrybuty do pola zapasowy przy użyciu automatycznie implementowanych właściwości `field` wartość docelowa. Poniższy kod dodaje `TimeLastLoaded` właściwości i oznacza je jako nie można serializować:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

Następnym krokiem jest dodawanie do aplikacji LoanApp kodu serializacji. Aby można było serializować klasy i zapisze go w pliku, użyj <xref:System.IO> i <xref:System.Runtime.Serialization.Formatters.Binary> przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do niezbędne przestrzeni nazw, jak pokazano w poniższym kodzie:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

Następnym krokiem jest Dodaj kod, aby deserializować obiektu z pliku po utworzeniu obiektu. Dodaj stałą do klasy dla danych serializacji. Nazwa pliku, jak pokazano w poniższym kodzie:

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

Następnie dodaj następujący kod po wierszu, który tworzy `TestLoan` obiektu:

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

Musisz najpierw sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy odczytanie pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku. Należy również konwertować z typu stream z typem obiektu pożyczki.

Następnie należy dodać kodu do serializacji klasy w pliku. Dodaj następujący kod po istniejący kod w `Main` metody:

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

W tym momencie możesz ponownie skompilować i uruchomić aplikację. Podczas pierwszego uruchomienia, zwróć uwagę, że odsetek rozpoczyna się w wersji 7.5, a następnie zmienia 7.1. Zamknij aplikację i uruchom go ponownie. Teraz aplikacja wyświetla komunikat, że ma odczytu zapisany plik, a stopie procentowej 7.1 nawet przed kod, który powoduje.

## <a name="see-also"></a>Zobacz także

 [Serializacja (C#)](index.md)  
 [Przewodnik programowania w języku C#](../..//index.md)  

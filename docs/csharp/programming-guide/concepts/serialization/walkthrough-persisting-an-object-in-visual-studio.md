---
title: 'Instruktaż: Utrwalanie obiektu przy użyciu C #'
ms.date: 04/26/2018
ms.openlocfilehash: 85c5d1b711180eda5734d5860d996242c6bc89d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167573"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Instruktaż: utrwalanie obiektu przy użyciu C\#

Serializacji można użyć do utrwalenia danych obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym wystąpieniu obiektu.

W tym instruktażu `Loan` utworzysz obiekt podstawowy i utrwalisz jego dane do pliku. Dane zostaną pobrane z pliku podczas ponownego tworzenia obiektu.

> [!IMPORTANT]
> W tym przykładzie tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta `Create` aplikacja musi mieć uprawnienia do folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja `Write` wymaga tylko uprawnień, mniejsze uprawnienia. Jeśli to możliwe, bezpieczniej jest utworzyć plik podczas `Read` wdrażania i przyznać uprawnienia tylko jednemu plikowi (zamiast utwórz uprawnienia dla folderu). Ponadto bezpieczniej jest zapisywać dane w folderach użytkowników niż w folderze głównym lub folderze Pliki programów.

> [!IMPORTANT]
> W tym przykładzie przechowuje dane w pliku w formacie binarnym. Formaty te nie powinny być używane w odniesieniu do poufnych danych, takich jak hasła lub informacje o karcie kredytowej.

## <a name="prerequisites"></a>Wymagania wstępne

- Aby utworzyć i uruchomić, zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).

- Zainstaluj swój ulubiony edytor kodu, jeśli jeszcze tego nie zrobiłeś.

> [!TIP]
> Chcesz zainstalować edytor kodów? [Wypróbuj program Visual Studio!](https://visualstudio.com/downloads)

- Przykład wymaga Języka C# 7.3. Zobacz [Wybieranie wersji językowej języka Języka C#](../../../language-reference/configure-language-version.md)

Przykładowy kod można sprawdzić w trybie online [w repozytorium github .NET .](https://github.com/dotnet/samples/tree/master/csharp/serialization)

## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki

Pierwszym krokiem jest `Loan` utworzenie klasy i aplikacji konsoli, która używa klasy:

1. Utwórz nową aplikację. Wpisz, `dotnet new console -o serialization` aby utworzyć nową aplikację `serialization`konsoli w podkatalogu o nazwie .
1. Otwórz aplikację w edytorze i dodaj `Loan.cs`nową klasę o nazwie .
1. Dodaj następujący kod `Loan` do swojej klasy:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Należy również utworzyć aplikację, która `Loan` używa klasy.

## <a name="serialize-the-loan-object"></a>Serializacja obiektu pożyczki

1. Otwórz plik `Program.cs`. Dodaj następujący kod:

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Dodaj program obsługi `PropertyChanged` zdarzeń dla zdarzenia i `Loan` kilka wierszy, aby zmodyfikować obiekt i wyświetlić zmiany. Możesz zobaczyć dodatki w następującym kodzie:

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

W tym momencie można uruchomić kod i zobaczyć bieżące dane wyjściowe:

```console
New customer value: Henry Clay
7.5
7.1
```

Uruchamianie tej aplikacji wielokrotnie zawsze zapisuje te same wartości. Nowy obiekt Pożyczka jest tworzony przy każdym uruchomieniu programu. W świecie rzeczywistym stopy procentowe zmieniają się okresowo, ale niekoniecznie za każdym razem, gdy aplikacja jest uruchamiana. Kod serializacji oznacza zachowanie najnowszej stopy procentowej między wystąpieniami aplikacji. W następnym kroku zrobisz tylko, że dodając serializacji do Pożyczki klasy.

## <a name="using-serialization-to-persist-the-object"></a>Używanie serializacji do utrwalania obiektu

Aby utrwalić wartości dla Klasy Pożyczki, należy `Serializable` najpierw oznaczyć klasę atrybutem. Dodaj następujący kod powyżej definicji klasy pożyczki:

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

Informuje <xref:System.SerializableAttribute> kompilator, że wszystko w klasie można utrwalić do pliku. Ponieważ `PropertyChanged` zdarzenie nie reprezentuje część wykresu obiektu, które powinny być przechowywane, nie powinny być serializowane. W ten sposób można serializować wszystkie obiekty, które są dołączone do tego zdarzenia. Można dodać <xref:System.NonSerializedAttribute> do deklaracji pola `PropertyChanged` dla programu obsługi zdarzeń.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

Począwszy od Języka C# 7.3, można dołączyć atrybuty do pola `field` zapasowego właściwości auto implementowane przy użyciu wartości docelowej. Poniższy kod dodaje `TimeLastLoaded` właściwość i oznacza ją jako nieserializowalną:

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp. Aby serializować klasę i zapisać ją do pliku, <xref:System.IO> należy <xref:System.Runtime.Serialization.Formatters.Binary> użyć i przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych obszarów nazw, jak pokazano w poniższym kodzie:

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

Następnym krokiem jest dodanie kodu do deserializacji obiektu z pliku podczas tworzenia obiektu. Dodaj stałą do klasy dla nazwy pliku danych serializowanych, jak pokazano w poniższym kodzie:

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Następnie dodaj następujący kod po wierszu, który tworzy `TestLoan` obiekt:

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Najpierw należy sprawdzić, czy plik istnieje. Jeśli istnieje, utwórz <xref:System.IO.Stream> klasę do odczytu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pliku binarnego i klasę, aby przetłumaczyć plik. Należy również przekonwertować z typu strumienia do typu Pożyczka typu obiektu.

Następnie należy dodać kod do serializacji klasy do pliku. Dodaj następujący kod po istniejącym `Main` kodzie w metodzie:

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

W tym momencie można ponownie utworzyć i uruchomić aplikację. Po raz pierwszy działa, należy zauważyć, że stopy procentowe zaczynają się od 7,5, a następnie zmienia się na 7,1. Zamknij aplikację, a następnie uruchom ją ponownie. Teraz aplikacja drukuje komunikat, że przeczytał zapisany plik, a stopa procentowa wynosi 7,1 jeszcze przed kodem, który go zmienia.

## <a name="see-also"></a>Zobacz też

- [Serializacja (C#)](index.md)
- [Przewodnik programowania języka C#](../..//index.md)

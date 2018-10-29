---
title: Najlepsze praktyki dotyczące wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6aa1049c531550687a2c6289ccd87e763ca2f58
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199633"
---
# <a name="best-practices-for-exceptions"></a>Najlepsze praktyki dotyczące wyjątków

Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji. W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.

## <a name="use-trycatchfinally-blocks"></a>Użyj bloki try/catch/finally

Użyj `try` / `catch` / `finally` bloki wokół kodu, który potencjalnie może generować wyjątek. 

W `catch` blokuje zawsze porządkować wyjątki od najbardziej specyficznych do najmniej specyficznych.

Użyj `finally` bloku, aby wyczyścić zasoby, czy można odzyskać, czy nie.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Obsługa typowe warunki bez zgłaszanie wyjątków

Warunki, które mogą wystąpić, ale może być wywołanie wyjątku, należy wziąć pod uwagę ich obsługę w sposób, który pozwoli uniknąć wyjątku. Na przykład, jeśli użytkownik próbuje zamknąć połączenie, które jest już zamknięty, uzyskasz `InvalidOperationException`. Można uniknąć, za pomocą `if` instrukcję, aby sprawdzić stan połączenia przed podjęciem próby je zamknąć.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Jeśli nie możesz sprawdzić stan połączenia przed zamknięciem, możesz przechwytywać `InvalidOperationException` wyjątku.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Metoda wyboru zależy od tego, jak często oczekuje się wystąpienia danego zdarzenia.

- Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku. Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.

- Wyszukaj warunki błędów w kodzie, jeśli zdarzenie występuje często i może być traktowane jako część normalnego wykonywania. Podczas sprawdzania dostępności typowe warunki błędów, mniej kodu jest wykonywanego, ponieważ pozwala uniknąć wyjątków.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Klasy należy projektować, dzięki czemu można uniknąć wyjątków

Klasa może zapewnić metody lub właściwości, które pozwalają uniknąć nawiązywania połączenia, które będą wyzwalać wyjątek. Na przykład <xref:System.IO.FileStream> klasa dostarcza metody pomagające ustalić, czy osiągnięto koniec pliku. Mogą one używane w celu uniknięcia wyjątek, który jest zgłaszany w przypadku odczytu poza końcem pliku. Poniższy przykład pokazuje, jak wykonać Odczyt do końca pliku bez powodowania wyjątek.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Innym sposobem na uniknięcie wyjątków jest zwracana wartość null dla ekstremalnie częstych przypadków błędów zamiast zgłaszać wyjątek. Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania. Zwracanie w takich przypadkach wartości null minimalizuje ich wpływ na wydajność aplikacji.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Zgłaszają wyjątki, zamiast zwracać kod błędu:

Wyjątki upewnij się, że awarie nie niezauważone ponieważ wywołanie kodu nie Sprawdź kod powrotny. 

## <a name="use-the-predefined-net-exception-types"></a>Użyj wstępnie zdefiniowanych typów wyjątków platformy .NET

Wprowadzenie nowej klasy wyjątku tylko wtedy, gdy nie ma zastosowania jednego wstępnie zdefiniowane. Na przykład:

- Throw <xref:System.InvalidOperationException> wyjątek, jeśli właściwość zestawu lub wywołanie metody nie jest odpowiednie bieżącego stanu obiektu.

- Throw <xref:System.ArgumentException> wyjątku lub jeden z wstępnie zdefiniowanych klas, które wynikają z <xref:System.ArgumentException> Jeśli zostaną przekazane nieprawidłowe parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Nazwy klas wyjątków koniec wyrazu `Exception`

Gdy konieczne jest niestandardowy wyjątek, nadaj mu nazwę odpowiednio i pochodzić z <xref:System.Exception> klasy. Na przykład:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Obejmują trzy konstruktory w klasach niestandardowy wyjątek

Użyj co najmniej trzech typowych konstruktorów, podczas tworzenia własnych klas wyjątków: konstruktora domyślnego, konstruktora przyjmującego komunikat w formacie ciągu oraz konstruktora przyjmującego komunikat w formacie ciągu i wyjątek wewnętrzny.

* <xref:System.Exception.%23ctor>, który używa wartości domyślnych.
  
* <xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat w formacie ciągu.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat w formacie ciągu i wyjątek wewnętrzny.  
  
Aby uzyskać przykład, zobacz [porady: wyjątki create user-defined](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Upewnij się, że wyjątku jest dostępny, gdy kod jest wykonywany zdalnie

Podczas tworzenia wyjątków zdefiniowanych przez użytkownika, upewnij się, że metadane dla wyjątków dostępne dla zdalnie wykonywanego kodu. 

Na przykład dotyczącej implementacji platformy .NET, które obsługują domen aplikacji, wyjątki mogą wystąpić w domenach aplikacji. Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod zgłaszający wyjątek. Aby domena aplikacji A mogła poprawnie przechwycić i obsłużyć wyjątek musi być w stanie znaleźć zestaw zawierający wyjątek zgłaszany przez domenę aplikacji B. Jeśli domena aplikacji B zgłosi wyjątek, który jest zawarty w zestawie, do jej podstawy aplikacji, ale nie w ramach podstawy aplikacji domeny aplikacji A, domena aplikacji A nie będzie można znaleźć wyjątku i środowisko uruchomieniowe języka wspólnego zgłosi <xref:System.IO.FileNotFoundException> wyjątku. Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:

- Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.

    \- lub —

- Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.

## <a name="use-grammatically-correct-error-messages"></a>Używać poprawnych gramatycznie komunikatów

Pisz wyczyść zdania i obejmują kończące znaki interpunkcyjne. Każde zdanie w ciągu przypisane do <xref:System.Exception.Message?displayProperty=nameWithType> właściwość powinien kończyć się kropką. Na przykład "przepełnienie tabeli dziennika." może być ciągiem odpowiedni komunikat.

## <a name="include-a-localized-string-message-in-every-exception"></a>Uwzględnij wiadomość zlokalizowany ciąg do każdego wyjątku

Komunikat o błędzie widziany przez użytkownika jest tworzony na podstawie <xref:System.Exception.Message?displayProperty=nameWithType> właściwości wyjątku, który został zgłoszony, a nie od nazwy klasy wyjątku. Zazwyczaj przypisanie wartości do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości, przekazując ciąg wiadomości do `message` argument [konstruktora wyjątków](xref:System.Exception.%23ctor%2A). 

W przypadku zlokalizowanych aplikacji należy Podaj ciąg zlokalizowany komunikat każdy wyjątek, który może zgłosić aplikacji. Pliki zasobów umożliwia zapewniają lokalizowane komunikaty o błędzie. Informacje na temat lokalizowanie aplikacji i pobieranie zlokalizowanych ciągów, zobacz [zasoby w aplikacjach pulpitu](../../framework/resources/index.md) i <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Niestandardowe wyjątki zapewniają dodatkowe właściwości, zgodnie z potrzebami

Podaj dodatkowe właściwości, dla wyjątku (oprócz ciąg niestandardowy komunikat) tylko wtedy, gdy istnieje scenariusz programowy, w których jest użyteczny dodatkowe informacje. Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwości.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Umieść throw — instrukcje, aby ślad stosu okaże się pomocna

Ślad stosu zaczyna się od instrukcji, gdy wyjątek jest wyrzucany i kończy się na `catch` instrukcję, która przechwytuje wyjątek.

## <a name="use-exception-builder-methods"></a>Używać metod konstruktora wyjątków

Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji. Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają. Na przykład:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
W niektórych przypadkach jest bardziej odpowiednie użycie konstruktora wyjątków w celu utworzenia wyjątku. Przykładem jest klasą globalnych <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Czyścić wyniki pośrednie podczas zgłaszania wyjątków

Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę. Na przykład jeśli kod, który przesyła pieniądze wycofania z jednego konta, a zdeponowanie na innym koncie, a wyjątek jest zgłaszany podczas wykonywania złożenia, nie chcesz wycofania do obowiązywać.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Jednym ze sposobów, aby obsłużyć taką sytuację jest przechwytywać wyjątki zgłaszane przez transakcję depozytu i wycofać wycofania.

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

Ten przykład ilustruje użycie `throw` ponownie zgłosić oryginalny wyjątek, który może ułatwić aby wywołujący mogli zobaczyć przyczyny rzeczywistego problemu bez konieczności zbadać <xref:System.Exception.InnerException> właściwości. Alternatywą jest nowy wyjątku i obejmują oryginalnego wyjątku, ponieważ wyjątek wewnętrzny:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed", innerException: ex)
    {
        From = from,
    To = to,
    Amount = amount
    };
}
```

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)

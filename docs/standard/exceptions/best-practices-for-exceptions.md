---
title: "Najlepsze praktyki dotyczące wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c5ea19077ff9ce8e36a33601b7e5e87c64afe60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-exceptions"></a>Najlepsze praktyki dotyczące wyjątków

Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji. W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i Tworzenie wyjątków.

## <a name="use-trycatchfinally-blocks"></a>Użyj bloki try/catch/finally

Użyj `try` / `catch` / `finally` bloki wokół kod, który może potencjalnie wygenerować wyjątek. 

W `catch` blokuje zawsze wyjątki w kolejności od najbardziej właściwe do najmniej specyficznych.

Użyj `finally` bloku, aby wyczyścić zasoby, czy użytkownik może odzyskać lub nie.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Obsługi typowe warunki bez zgłaszanie wyjątków

Warunki, które mogą wystąpić, ale może powodować powstanie wyjątku, należy rozważyć ich obsługę w taki sposób, aby uniknąć tego wyjątku. Na przykład, Jeśli spróbujesz zamknąć połączenie, które jest już zamknięty, otrzymasz `InvalidOperationException`. Można uniknąć który za pomocą `if` instrukcji, aby sprawdzić stan połączenia przed podjęciem próby go zamknąć.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Jeśli nie zaznaczysz stan połączenia przed zamknięciem, można przechwycić `InvalidOperationException` wyjątku.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Wybierz metodę zależy od tego, częstotliwość wystąpienie zdarzenia.

- Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku. Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.

- Sprawdź, czy warunki błędów w kodzie, jeśli zdarzenie wykonywany jest rutynowo i może zostać uznana za część normalnego wykonywania. Podczas sprawdzania dostępności typowe warunki błędów, mniejsza ilość kodu jest wykonywana, ponieważ uniknąć wyjątków.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Projektowanie klas, aby uniknąć wyjątków

Klasa może zapewnić metody lub właściwości, które pozwalają uniknąć nawiązywania połączenia, który może powodować powstanie wyjątku. Na przykład <xref:System.IO.FileStream> klasa dostarcza metody, które pomagają w ustaleniu, czy osiągnięto koniec pliku. Mogą one używane w celu uniknięcia wyjątek, który jest generowany, jeśli odczytu poza końcem pliku. Poniższy przykład pokazuje, jak można odczytać na końcu pliku bez wyzwalania Wystąpił wyjątek.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Innym sposobem uniknięcia wyjątków jest zwracana wartość null dla bardzo typowych przypadkach błąd zamiast generowania wyjątku. Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania. Zwracanie w takich przypadkach wartości null minimalizuje ich wpływ na wydajność aplikacji.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Zgłaszanie wyjątków zamiast zwróciło kod błędu

Wyjątki upewnij się, że błędy nie niezauważone ponieważ wywoływanie kodu nie Sprawdź kod powrotu. 

## <a name="use-the-predefined-net-exception-types"></a>Użyj wstępnie zdefiniowanych typów wyjątków .NET

Wprowadzenie nowej klasy wyjątku tylko wtedy, gdy jeden wstępnie zdefiniowanych nie ma zastosowania. Na przykład:

- Throw <xref:System.InvalidOperationException> wyjątek, jeśli właściwość zestawu lub wywołanie metody nie jest odpowiedni podane bieżącego stanu obiektu.

- Throw <xref:System.ArgumentException> wyjątku lub jednej z wstępnie zdefiniowanych klas pochodzących od <xref:System.ArgumentException> Jeżeli nie przekazano nieprawidłowe parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Nazwy klasy wyjątków zakończenia wyraz`Exception`

Gdy konieczne jest niestandardowy wyjątek, odpowiednio nazwę i pochodzi ona z <xref:System.Exception> klasy. Na przykład:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Obejmują trzy konstruktorów w klasach niestandardowego wyjątku

Użyj co najmniej trzy konstruktorów wspólnej podczas tworzenia własnych klas wyjątek: konstruktora domyślnego konstruktora przyjmującego ciąg komunikatu i konstruktora przyjmującego ciąg komunikatu i wyjątek wewnętrzny.

* <xref:System.Exception.%23ctor>, które są używane wartości domyślne.
  
* <xref:System.Exception.%23ctor%28System.String%29>, która akceptuje ciąg komunikatu.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, która akceptuje ciąg komunikatu i wyjątek wewnętrzny.  
  
Na przykład zobacz [porady: wyjątki Create User-Defined](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Upewnij się, dane wyjątku jest dostępna, gdy kod jest wykonywany zdalnie

Podczas tworzenia wyjątki zdefiniowane przez użytkownika, upewnij się, że metadane dla wyjątków jest dostępny do kodu, który jest wykonywany zdalnie. 

Na przykład w implementacjach .NET, które obsługują domen aplikacji, wyjątki między domenami aplikacji. Załóżmy, że domena aplikacji A tworzy aplikację domeny B, który wykonuje kod, który zgłasza wyjątek. Domeny aplikacji A Aby prawidłowo wychwycić i obsłużyć wyjątek musi być w stanie odnaleźć zestawu, który zawiera wyjątku zgłoszonego przez B. domeny aplikacji Jeśli aplikacja domena B zgłasza wyjątek, który jest zawarty w zestawie w swojej bazie aplikacji, ale nie w domenie aplikacji, A baza aplikacji, domena aplikacji, A nie będzie można znaleźć w wyjątku i zgłosi środowisko uruchomieniowe języka wspólnego <xref:System.IO.FileNotFoundException> wyjątku. Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:

- Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.

    \-lub -

- Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.

## <a name="include-a-localized-description-string-in-every-exception"></a>Zawierają ciąg zlokalizowany opis w każdym wyjątku

Użytkownik zobaczy następujący komunikat o błędzie jest uzyskiwany z ciąg opisu wyjątku, który został zgłoszony, a nie z nazwa klasy wyjątku.

## <a name="use-grammatically-correct-error-messages"></a>Użyj gramatycznie Popraw komunikaty o błędach

Zapisz wyczyść zdań i dołączyć końcowy znaków interpunkcyjnych. Każde zdanie w ciągu opisu wyjątku powinno być zakończone kropką. Na przykład "w tabeli dziennika jest przepełniony." może być ciągiem opis.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>W niestandardowymi wyjątkami udostępniają dodatkowe właściwości, w razie potrzeby

Podaj dodatkowe właściwości dla wyjątku (oprócz ciąg opisu) tylko wtedy, gdy programowe scenariusz, w którym przydaje się dodatkowe informacje. Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwości.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Miejsce throw — instrukcje, aby ślad stosu okaże się pomocna

Ślad stosu zaczyna się od instrukcji, gdzie wyjątek jest zgłaszany i kończy się na `catch` instrukcji, która przechwytuje wyjątek.

## <a name="use-exception-builder-methods"></a>Użyj metody konstruktora wyjątku

Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji. Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają. Na przykład:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
W niektórych przypadkach jest bardziej odpowiednia umożliwia utworzenie wyjątek obsługi wyjątku konstruktora. Przykładem jest klasa wyjątków globalne <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Wyczyść wyniki pośrednie po zgłoszeniu wyjątku

Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę. Na przykład jeśli kod, który przesyła pieniędzy wycofania z jednego konta i złożenie na innym koncie, a wyjątek podczas wykonywania złożenia, nie mają wycofania do obowiązują.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Jednym ze sposobów obsłużyć taką sytuację jest catch wszelkie wyjątki zgłaszane przez transakcji wpłaty i wycofać wycofanie.

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

W tym przykładzie przedstawiono użycie `throw` ponowne wygenerowanie oryginalnego wyjątków, które mogą ułatwić wywołań wyświetlić rzeczywiste przyczyną problemu bez konieczności zbadać <xref:System.Exception.InnerException> właściwości. Alternatywą jest zgłoszenie wyjątku nowy i zawiera pierwotny wyjątek jako wyjątek wewnętrzny:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Zobacz też  
[Wyjątki](index.md)

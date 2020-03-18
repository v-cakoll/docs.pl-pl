---
title: Najważniejsze wskazówki dotyczące wyjątków - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160173"
---
# <a name="best-practices-for-exceptions"></a>Najważniejsze wskazówki dotyczące wyjątków

Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji. W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a>Użyj try/catch/finally blocks, aby odzyskać od błędów lub zwolnić zasoby

`try` / Użyj `catch` bloków wokół kodu, który może potencjalnie wygenerować wyjątek ***i*** kod można odzyskać z tego wyjątku. W `catch` blokach zawsze porządku wyjątki od najbardziej pochodnych do najmniej pochodnych. Wszystkie wyjątki wynikają <xref:System.Exception>z . Więcej pochodnych wyjątków nie są obsługiwane przez catch klauzuli, która jest poprzedzona catch klauzuli dla klasy wyjątku podstawowego. Gdy kod nie można odzyskać z wyjątku, nie przechwycić tego wyjątku. Włącz metody dalej stosu wywołań, aby odzyskać, jeśli to możliwe.

Oczyść zasoby `using` przydzielone `finally` za pomocą instrukcji lub bloków. Wolisz `using` instrukcje do automatycznego oczyszczania zasobów, gdy wyjątki są generowane. Użyj `finally` bloków, aby oczyścić <xref:System.IDisposable>zasoby, które nie implementują . Kod w `finally` klauzuli jest prawie zawsze wykonywane nawet wtedy, gdy wyjątki są generowane.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Obsługa typowych warunków bez zgłaszania wyjątków

W przypadku warunków, które mogą wystąpić, ale może wyzwolić wyjątek, należy rozważyć obsługę ich w sposób, który pozwoli uniknąć wyjątku. Na przykład, jeśli spróbujesz zamknąć połączenie, które jest `InvalidOperationException`już zamknięte, otrzymasz plik . Można tego uniknąć za `if` pomocą instrukcji, aby sprawdzić stan połączenia przed próbą zamknięcia go.

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

Jeśli nie sprawdzić stan połączenia przed zamknięciem, `InvalidOperationException` można przechwycić wyjątek.

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

Metoda do wybrania zależy od tego, jak często można oczekiwać wystąpienia zdarzenia.

- Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku. Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.

- Sprawdź, czy warunki błędów w kodzie, jeśli zdarzenie dzieje się rutynowo i może być uznane za część normalnego wykonywania. Podczas sprawdzania typowych warunków błędu wykonywany jest mniej kodu, ponieważ można uniknąć wyjątków.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Klasy projektowania, dzięki czemu można uniknąć wyjątków

Klasa może zapewnić metody lub właściwości, które umożliwiają uniknięcie wywołania, które wyzwoliłoby wyjątek. Na przykład <xref:System.IO.FileStream> klasa zawiera metody, które pomagają określić, czy osiągnięto koniec pliku. Mogą one służyć do uniknięcia wyjątku, który jest generowany, jeśli czytasz poza końcem pliku. W poniższym przykładzie pokazano, jak odczytywać na końcu pliku bez wyzwalania wyjątku.

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

Innym sposobem uniknięcia wyjątków jest zwrócenie wartości null (lub domyślnej) dla bardzo typowych przypadków błędów zamiast zgłaszania wyjątku. Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania. Zwracając null (lub domyślnie) w takich przypadkach, można zminimalizować wpływ na wydajność do aplikacji.

W przypadku typów wartości, czy użyć `Nullable<T>` lub domyślnie jako wskaźnik błędu jest coś do rozważenia dla danej aplikacji. Za `Nullable<Guid>`pomocą `default` , `null` staje `Guid.Empty`się zamiast . Czasami dodawanie `Nullable<T>` może uczynić go jaśniejszym, gdy wartość jest obecna lub nieobecna. Innym razem `Nullable<T>` dodawanie można utworzyć dodatkowe sprawy, aby sprawdzić, które nie są konieczne i służyć tylko do tworzenia potencjalnych źródeł błędów.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Zgłaszanie wyjątków zamiast zwracania kodu błędu

Wyjątki upewnij się, że błędy nie pozostają niezauważone, ponieważ kod wywołujący nie sprawdzić kod zwrotny.

## <a name="use-the-predefined-net-exception-types"></a>Używanie wstępnie zdefiniowanych typów wyjątków .NET

Wprowadź nową klasę wyjątku tylko wtedy, gdy wstępnie zdefiniowana nie ma zastosowania. Przykład:

- Zgłaszanie <xref:System.InvalidOperationException> wyjątku, jeśli zestaw właściwości lub wywołanie metody nie jest właściwe, biorąc pod uwagę bieżący stan obiektu.

- Zgłaszanie <xref:System.ArgumentException> wyjątku lub jednej ze wstępnie zdefiniowanych klas, które pochodzą z <xref:System.ArgumentException> jeśli są przekazywane nieprawidłowe parametry.

## <a name="end-exception-class-names-with-the-word-exception"></a>Kończenie nazw klas wyjątków słowem`Exception`

Gdy wyjątek niestandardowy jest konieczne, należy odpowiednio nazwać <xref:System.Exception> go i wyprowadzić go z klasy. Przykład:

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a>Dołącz trzy konstruktory w niestandardowych klasach wyjątków

Użyj co najmniej trzech typowych konstruktorów podczas tworzenia własnych klas wyjątków: konstruktora bezparametrowego, konstruktora, który przyjmuje komunikat ciągu i konstruktora, który przyjmuje komunikat ciągu i wyjątek wewnętrzny.

- <xref:System.Exception.%23ctor>, który używa wartości domyślnych.

- <xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat ciągu.

- <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat ciągu i wyjątek wewnętrzny.

Na przykład zobacz [Jak: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Upewnij się, że dane wyjątku są dostępne, gdy kod jest wykonywany zdalnie

Podczas tworzenia wyjątków zdefiniowanych przez użytkownika upewnij się, że metadane wyjątków są dostępne dla kodu, który jest wykonywany zdalnie.

Na przykład w implementacjach .NET, które obsługują domeny aplikacji, mogą wystąpić wyjątki w domenach aplikacji. Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod, który zgłasza wyjątek. Dla domeny aplikacji A poprawnie złapać i obsługiwać wyjątek, musi być w stanie znaleźć zestaw, który zawiera wyjątek zgłoszony przez domenę aplikacji B. Jeśli domena aplikacji B zgłasza wyjątek, który znajduje się w zestawie w ramach jego bazy aplikacji, ale nie w ramach bazy aplikacji domeny aplikacji <xref:System.IO.FileNotFoundException> A, domena aplikacji A nie będzie mógł znaleźć wyjątek, a czas wykonywania języka wspólnego spowoduje wyjątek. Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:

- Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.

    \-lub -

- Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.

## <a name="use-grammatically-correct-error-messages"></a>Używanie komunikatów o błędach poprawne gramatycznie

Napisz jasne zdania i dołącz końcową interpunkcję. Każde zdanie w ciągu przypisanym do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości powinno zakończyć się kropką. Na przykład "Tabela dziennika została przepełniona." będzie odpowiedni ciąg komunikatu.

## <a name="include-a-localized-string-message-in-every-exception"></a>Dołączanie zlokalizowanej wiadomości ciągu w każdym wyjątku

Komunikat o błędzie, który widzi <xref:System.Exception.Message?displayProperty=nameWithType> użytkownik pochodzi od właściwości wyjątku, który został zgłoszony, a nie od nazwy klasy wyjątku. Zazwyczaj można przypisać wartość do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości, przekazując ciąg `message` komunikatu do argumentu [konstruktora wyjątku](xref:System.Exception.%23ctor%2A).

W przypadku zlokalizowanych aplikacji należy podać zlokalizowany ciąg komunikatów dla każdego wyjątku, który aplikacja może zgłosić. Pliki zasobów służy do dostarczania zlokalizowanych komunikatów o błędach. Aby uzyskać informacje na temat lokalizowania aplikacji i pobierania zlokalizowanych ciągów, zobacz następujące artykuły:

- [Instrukcje: tworzenie wyjątków zdefiniowanych przez użytkownika z zastosowaniem zlokalizowanych komunikatów o wyjątkach](how-to-create-localized-exception-messages.md)
- [Zasoby w aplikacjach klasycznych](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>W wyjątkach niestandardowych podaj dodatkowe właściwości zgodnie z potrzebami

Podaj dodatkowe właściwości dla wyjątku (oprócz niestandardowego ciągu komunikatu) tylko wtedy, gdy istnieje scenariusz programowy, w którym przydatne są dodatkowe informacje. Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwość.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Umieść instrukcje throw, aby śledzenie stosu było pomocne

Śledzenie stosu rozpoczyna się od instrukcji, `catch` gdzie wyjątek jest zgłaszany i kończy się na instrukcji, która przechwytuje wyjątek.

## <a name="use-exception-builder-methods"></a>Używanie metod konstruktowania wyjątków

Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji. Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają. Przykład:

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

W niektórych przypadkach jest bardziej odpowiednie do użycia konstruktora wyjątku do tworzenia wyjątku. Przykładem jest klasa wyjątków <xref:System.ArgumentException>globalnych, takich jak .

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a>Przywracanie stanu, gdy metody nie są ukończone z powodu wyjątków

Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę. Na przykład, jeśli masz kod, który przelewa pieniądze, wypłacając pieniądze z jednego konta i deponując na innym koncie, a podczas wykonywania wpłaty pojawia się wyjątek, nie chcesz, aby wypłata pozostała w mocy.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

Powyższa metoda nie powoduje bezpośrednio żadnych wyjątków, ale musi być napisana defensywnie, aby w przypadku niepowodzenia operacji wpłaty wycofanie zostało odwrócone.

Jednym ze sposobów radzenia sobie z tą sytuacją jest złapanie wszelkich wyjątków zgłoszonych przez transakcję wpłaty i wycofanie wypłaty.

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

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

W tym przykładzie przedstawiono `throw` użycie do ponownego zgłosić oryginalny wyjątek, który może ułatwić wywołujących, aby zobaczyć <xref:System.Exception.InnerException> rzeczywistą przyczynę problemu bez konieczności badania właściwości. Alternatywą jest zgłosić nowy wyjątek i dołączyć oryginalny wyjątek jako wyjątek wewnętrzny:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)

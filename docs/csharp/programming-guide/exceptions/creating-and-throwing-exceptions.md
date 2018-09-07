---
title: Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 2e792a230ccead5d9a73f9b78a83d57738c31085
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071521"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)
Wyjątki są używane do wskazania, że wystąpił błąd podczas uruchamiania programu. Obiekty wyjątków, które opisują błąd są tworzone a następnie *zgłoszony* z [throw](../../../csharp/language-reference/keywords/throw.md) — słowo kluczowe. Środowisko uruchomieniowe wyszukuje następnie najbardziej zgodne obsługi wyjątków.  
  
 Programiści powinien zgłaszać wyjątki, gdy dla jednego lub więcej z następujących warunków jest spełniony:  
  
-   Metoda nie może ukończyć jej zdefiniowane funkcje.  
  
     Na przykład, jeśli parametr do metody ma nieprawidłową wartość:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Nieodpowiednie do obiektu rozmowy, na podstawie stanu obiektu.  
  
     Przykładem może próbować zapis pliku tylko do odczytu. W przypadkach, gdy stan obiektu nie zezwala na operację, należy zgłaszać wystąpienie <xref:System.InvalidOperationException> lub obiektu oparte na typem pochodnym tej klasy. Jest to przykład metody, która zgłasza <xref:System.InvalidOperationException> obiektu:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Gdy argument do metody, powoduje wyjątek.  
  
     W tym przypadku oryginalnego wyjątku powinien zostać przechwycony i <xref:System.ArgumentException> można utworzyć wystąpienia. Oryginalny wyjątek powinien zostać przekazany do konstruktora obiektu <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametru:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Wyjątki zawiera właściwość o nazwie <xref:System.Exception.StackTrace%2A>. Ten ciąg zawiera nazwę metody na bieżący stos wywołań, wraz z pliku nazwa i numer wiersza gdzie dla każdej metody wystąpił wyjątek. A <xref:System.Exception.StackTrace%2A> obiekt zostanie utworzony automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) od momentu `throw` instrukcji, tak aby musi być zgłaszane wyjątki od punktu, w którym powinna zacząć się ślad stosu.  
  
 Wszystkie wyjątki zawiera właściwość o nazwie <xref:System.Exception.Message%2A>. Ten ciąg powinna być równa wyjaśnienia przyczyn, dla wyjątku. Należy pamiętać, że informacje, które są wrażliwe na zabezpieczeń nie należy umieścić w treści wiadomości. Oprócz <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> zawiera właściwość o nazwie <xref:System.ArgumentException.ParamName%2A> , należy ustawić nazwę argumentu, który spowodował zgłoszenie wyjątku. W przypadku metoda ustawiająca właściwości <xref:System.ArgumentException.ParamName%2A> powinna być równa `value`.  
  
 Metody publiczne i chronione składowe powinny zgłaszać wyjątki, zawsze wtedy, gdy ich nie można ukończyć ich zamierzonych funkcji. Klasy wyjątków, który jest generowany, powinien być bardziej konkretny od pozostałych wyjątków, dostępności, która pasuje do warunków błędów. Te wyjątki powinny być udokumentowane w ramach funkcji klasy i klas pochodnych lub aktualizacje do oryginalnej klasy powinien zachować takie samo zachowanie zgodności z poprzednimi wersjami.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Czynności, aby uniknąć podczas zgłaszania wyjątków  
 Poniższa lista zawiera wskazówki, aby uniknąć podczas zgłaszania wyjątków:  
  
-   Wyjątki nie powinny umożliwiające zmianę przepływu programu, w ramach wykonywania zwykłych. Wyjątków należy używać tylko do raportowania i obsługi błędów.  
  
-   Wyjątki nie powinien być zwracany jako wartość zwracana lub parametr zamiast zgłaszane.  
  
-   Nie zgłaszają wyjątków <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, lub <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> celowo z kodu źródłowego.  
  
-   Nie należy tworzyć wyjątki, które mogą być generowane w trybie debugowania, ale nie tryb wydania. Aby zidentyfikować błędy czasu wykonywania w fazie opracowywania, należy użyć debugowania potwierdzenia.  
  
## <a name="defining-exception-classes"></a>Definiowanie klasy wyjątków  
 Programy może zgłosić klasy wstępnie zdefiniowany wyjątek <xref:System> przestrzeni nazw (z wyjątkiem sytuacji, gdy wcześniej wspomniano), lub Utwórz własne klasy wyjątków, wynikające z <xref:System.Exception>. W klasach pochodnych należy zdefiniować co najmniej cztery konstruktory: jeden domyślny konstruktor, który ustawia właściwości wiadomości oraz jedną, która ustawia zarówno <xref:System.Exception.Message%2A> i <xref:System.Exception.InnerException%2A> właściwości. Czwarty Konstruktor jest używany do serializacji wyjątku. Nowe klasy wyjątku powinien być możliwy do serializacji. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Nowe właściwości powinny być dodane tylko do klasy wyjątku, gdy dane, które zapewniają przydaje się do rozpoznawania wyjątku. Jeśli zostaną dodane do klasy pochodnej wyjątek `ToString()` powinna zostać zastąpiona w celu zwracania informacji dodano.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
- [Hierarchia wyjątków](https://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
- [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)

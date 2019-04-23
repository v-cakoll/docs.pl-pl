---
title: Tworzenie i zgłaszanie wyjątków - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 7a99afa92c7b2cc19933eded8e06e6d8f2ce7562
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979371"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)
Wyjątki są używane do wskazania, że wystąpił błąd podczas uruchamiania programu. Obiekty wyjątków, które opisują błąd są tworzone a następnie *zgłoszony* z [throw](../../../csharp/language-reference/keywords/throw.md) — słowo kluczowe. Środowisko uruchomieniowe wyszukuje następnie najbardziej zgodne obsługi wyjątków.  
  
 Programiści powinien zgłaszać wyjątki, gdy dla jednego lub więcej z następujących warunków jest spełniony:  
  
-   Metoda nie może ukończyć jej zdefiniowane funkcje.  
  
     Na przykład, jeśli parametr do metody ma nieprawidłową wartość:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
-   Nieodpowiednie do obiektu rozmowy, na podstawie stanu obiektu.  
  
     Przykładem może próbować zapis pliku tylko do odczytu. W przypadkach, gdy stan obiektu nie zezwala na operację, należy zgłaszać wystąpienie <xref:System.InvalidOperationException> lub obiektu oparte na typem pochodnym tej klasy. Jest to przykład metody, która zgłasza <xref:System.InvalidOperationException> obiektu:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
-   Gdy argument do metody, powoduje wyjątek.  
  
     W tym przypadku oryginalnego wyjątku powinien zostać przechwycony i <xref:System.ArgumentException> można utworzyć wystąpienia. Oryginalny wyjątek powinien zostać przekazany do konstruktora obiektu <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametru:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Wyjątki zawiera właściwość o nazwie <xref:System.Exception.StackTrace%2A>. Ten ciąg zawiera nazwę metody na bieżący stos wywołań, wraz z pliku nazwa i numer wiersza gdzie dla każdej metody wystąpił wyjątek. A <xref:System.Exception.StackTrace%2A> obiekt zostanie utworzony automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) od momentu `throw` instrukcji, tak aby musi być zgłaszane wyjątki od punktu, w którym powinna zacząć się ślad stosu.  
  
 Wszystkie wyjątki zawiera właściwość o nazwie <xref:System.Exception.Message%2A>. Ten ciąg powinna być równa wyjaśnienia przyczyn, dla wyjątku. Należy pamiętać, że informacje, które są wrażliwe na zabezpieczeń nie należy umieścić w treści wiadomości. Oprócz <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> zawiera właściwość o nazwie <xref:System.ArgumentException.ParamName%2A> , należy ustawić nazwę argumentu, który spowodował zgłoszenie wyjątku. W przypadku metoda ustawiająca właściwości <xref:System.ArgumentException.ParamName%2A> powinna być równa `value`.  
  
 Publiczne i chronione metody należy zgłaszać wyjątki, zawsze wtedy, gdy ich nie można ukończyć ich zamierzonych funkcji. Klasy wyjątków, który jest generowany, powinien być bardziej konkretny od pozostałych wyjątków, dostępności, która pasuje do warunków błędów. Te wyjątki powinny być udokumentowane w ramach funkcji klasy i klas pochodnych lub aktualizacje do oryginalnej klasy powinien zachować takie samo zachowanie zgodności z poprzednimi wersjami.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Czynności, aby uniknąć podczas zgłaszania wyjątków  
 Poniższa lista zawiera wskazówki, aby uniknąć podczas zgłaszania wyjątków:  
  
-   Wyjątki nie powinny umożliwiające zmianę przepływu programu, w ramach wykonywania zwykłych. Wyjątków należy używać tylko do raportowania i obsługi błędów.  
  
-   Wyjątki nie powinien być zwracany jako wartość zwracana lub parametr zamiast zgłaszane.  
  
-   Nie zgłaszają wyjątków <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, lub <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> celowo z kodu źródłowego.  
  
-   Nie należy tworzyć wyjątki, które mogą być generowane w trybie debugowania, ale nie tryb wydania. Aby zidentyfikować błędy czasu wykonywania w fazie opracowywania, należy użyć debugowania potwierdzenia.  
  
## <a name="defining-exception-classes"></a>Definiowanie klasy wyjątków  
 Programy może zgłosić klasy wstępnie zdefiniowany wyjątek <xref:System> przestrzeni nazw (z wyjątkiem sytuacji, gdy wcześniej wspomniano), lub Utwórz własne klasy wyjątków, wynikające z <xref:System.Exception>. W klasach pochodnych należy zdefiniować co najmniej cztery konstruktory: jeden konstruktor bez parametrów, który ustawia właściwości wiadomości i jedną, która ustawia zarówno <xref:System.Exception.Message%2A> i <xref:System.Exception.InnerException%2A> właściwości. Czwarty Konstruktor jest używany do serializacji wyjątku. Nowe klasy wyjątku powinien być możliwy do serializacji. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Nowe właściwości powinny być dodane tylko do klasy wyjątku, gdy dane, które zapewniają przydaje się do rozpoznawania wyjątku. Jeśli zostaną dodane do klasy pochodnej wyjątek `ToString()` powinna zostać zastąpiona w celu zwracania informacji dodano.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) i [instrukcji "throw"](~/_csharplang/spec/statements.md#the-throw-statement) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
- [Hierarchia wyjątków](../../../standard/exceptions/index.md)
- [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)

---
title: "Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4008323d264c02e0417e775077958f857ceed31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Tworzenie i zgłaszanie wyjątków (Przewodnik programowania w języku C#)
Wyjątki są używane do wskazywania, wystąpił błąd podczas uruchamiania programu. Obiekty wyjątków, które opisują wystąpił błąd, są tworzone i następnie *zgłoszony* z [throw](../../../csharp/language-reference/keywords/throw.md) — słowo kluczowe. Środowisko uruchomieniowe wyszukuje najbardziej zgodne obsługi wyjątków.  
  
 Programiści powinien zgłosić wyjątek przy jednej lub więcej poniższe warunki są spełnione:  
  
-   Metoda nie może ukończyć jej określonych funkcji.  
  
     Na przykład, jeśli parametr metody ma nieprawidłową wartość:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Niewłaściwe wywołania do obiektu złożonych, na podstawie stanu obiektu.  
  
     Przykładem może być próby zapisu do pliku tylko do odczytu. W przypadkach, gdy stan obiektu nie zezwala na operację throw wystąpienia <xref:System.InvalidOperationException> lub oparte na pochodnym tej klasy obiektu. To jest przykład metody, która zgłasza <xref:System.InvalidOperationException> obiektu:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Jeśli argument do metody powoduje zgłoszenie wyjątku.  
  
     W takim przypadku przechwycony wyjątek oryginalnego i <xref:System.ArgumentException> można utworzyć wystąpienia. Pierwotny wyjątek powinien zostać przekazany do konstruktora obiektu <xref:System.ArgumentException> jako <xref:System.Exception.InnerException%2A> parametru:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Wyjątki zawiera właściwości o nazwie <xref:System.Exception.StackTrace%2A>. Ten ciąg zawiera nazwę metody dla bieżącego stosu wywołań, wraz z pliku nazwę i numer wiersza gdy wyjątek został zgłoszony dla każdej metody. A <xref:System.Exception.StackTrace%2A> obiekt jest tworzony automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) od punktu `throw` instrukcji, dzięki czemu wyjątek od punktu, w którym powinny one zacząć ślad stosu.  
  
 Wszystkie wyjątki zawiera właściwości o nazwie <xref:System.Exception.Message%2A>. Ten ciąg powinien mieć ustawioną wyjaśnienia przyczyn dla wyjątku. Należy pamiętać, że informacje poufne z zabezpieczeniami nie należy umieścić w treści wiadomości. Oprócz <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> zawiera właściwość o nazwie <xref:System.ArgumentException.ParamName%2A> która powinna być równa Nazwa argumentu, który spowodował wyjątek zostanie wygenerowany. W przypadku metody ustawiającej właściwość <xref:System.ArgumentException.ParamName%2A> powinien być ustawiony na `value`.  
  
 Metody publiczne i chronione elementy Członkowskie powinny zgłaszają wyjątki, zawsze, gdy ich nie można ukończyć ich zamierzonej funkcji. Klasy wyjątków, który jest zgłaszany powinna być najbardziej konkretny wyjątek dostępne, który pasuje do warunków błędów. Te wyjątki powinny być udokumentowane w ramach funkcji klasy i klasy pochodne lub aktualizacje do oryginalnej klasy pozostają takie samo zachowanie zgodności z poprzednimi wersjami.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Czynności, aby uniknąć generowania wyjątków  
 Poniższa lista zawiera wskazówki, aby uniknąć generowania wyjątków:  
  
-   Wyjątki nie powinny umożliwiające zmianę w ramach wykonywania zwykłych przepływ programu. Wyjątki należy używać tylko do raportu i obsługi błędów.  
  
-   Wyjątki nie powinny być zwracane jako zwracana wartość lub parametr zamiast został zgłoszony.  
  
-   Nie zgłaszają <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, lub <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> celowo w kodzie źródłowym.  
  
-   Nie należy tworzyć wyjątki, które może zostać wygenerowany w trybie debugowania, ale nie zwalnia tryb. Aby zidentyfikować błędów czasu wykonywania w fazie projektowania, użyj debugowania potwierdzenia.  
  
## <a name="defining-exception-classes"></a>Definiowanie klasy wyjątków  
 Programy mogą zgłaszać klasy wstępnie zdefiniowany wyjątek <xref:System> przestrzeni nazw (inaczej w przypadku gdy wcześniej), lub utworzyć własne klasy wyjątków wynikających z <xref:System.Exception>. Klasy pochodne należy zdefiniować co najmniej cztery konstruktory: jeden domyślny konstruktor, który ustawia właściwości wiadomości i jedną, która ustawia zarówno <xref:System.Exception.Message%2A> i <xref:System.Exception.InnerException%2A> właściwości. Czwarty Konstruktor jest używany do serializacji wyjątek. Nowe klasy wyjątku powinien być możliwy do serializacji. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Nowe właściwości powinny tylko dodany do klasy wyjątku po dane, które zapewniają przydaje się do rozpoznawania wyjątek. Jeśli zostaną dodane do klasy pochodnej wyjątek `ToString()` powinna zostać zastąpiona w celu zwracać dodano informacje.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
 [Hierarchia wyjątków](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)

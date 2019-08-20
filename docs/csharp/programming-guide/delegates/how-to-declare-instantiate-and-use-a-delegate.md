---
title: 'Instrukcje: Deklarowanie, tworzenie wystąpienia i używanie przewodnika C# po programowaniu delegata'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 565ae2a6c42de57570f564edc9d0bde5cab8efa8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590628"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Instrukcje: Deklarowanie, tworzenie wystąpienia i Używanie delegataC# (Przewodnik programowania)
W C# 1,0 i nowszych można zadeklarować delegatów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C#2,0 zapewnia prostszy sposób pisania poprzedniej deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 W C# 2,0 i nowszych jest również możliwe użycie anonimowej metody do zadeklarowania i zainicjowania delegata [](../../language-reference/keywords/delegate.md), jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 W C# 3,0 i nowszych Delegaty mogą być również deklarowane i tworzone przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład ilustruje deklarowanie, Tworzenie wystąpień i Używanie delegata. `BookDB` Klasa hermetyzuje bazę danych księgarni, która obsługuje bazę danych książek. Udostępnia ona metodę, `ProcessPaperbackBooks`która znajduje wszystkie książki drukowanego podręcznika w bazie danych i wywołuje delegata dla każdego z nich. Typ, który jest używany, ma `ProcessBookDelegate`nazwę. `delegate` `Test` Klasa używa tej klasy do drukowania tytułów i średniej ceny książek drukowanego podręcznika.  
  
 Użycie delegatów promuje dobre rozdzielenie funkcjonalności między bazą danych księgarni i kodem klienta. Kod klienta nie ma informacji o tym, w jaki sposób są przechowywane książki lub jak kod księgarni znajduje książki drukowanego podręcznika. Kod księgarni nie ma informacji o tym, jakie przetwarzanie jest wykonywane w książkach drukowanego podręcznika po ich znalezieniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Deklarowanie delegata.  
  
     Poniższa instrukcja deklaruje nowy typ delegata.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Każdy typ delegata zawiera informacje o liczbie i typach argumentów oraz typ zwracanej wartości metod, które mogą być hermetyzowane. Zawsze, gdy wymagany jest nowy zestaw typów argumentów lub typ wartości zwracanej, musi zostać zadeklarowany nowy typ delegata.  
  
- Utworzenie wystąpienia obiektu delegowanego.  
  
     Po zadeklarowaniu typu delegata należy utworzyć obiekt delegata i skojarzyć go z określoną metodą. W poprzednim przykładzie należy to zrobić, przekazując `PrintTitle` metodę `ProcessPaperbackBooks` do metody, jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Spowoduje to utworzenie nowego obiektu delegata skojarzonego z [](../../language-reference/keywords/static.md) metodą `Test.PrintTitle`statyczną. Podobnie Metoda `AddBookToTotal` niestatyczna w obiekcie `totaller` jest przenoszona jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     W obu przypadkach nowy obiekt delegata jest przenoszona do `ProcessPaperbackBooks` metody.  
  
     Po utworzeniu delegata Metoda jest skojarzona z nigdy zmianami; obiekty delegatów są niezmienne.  
  
- Wywoływanie delegata.  
  
     Po utworzeniu obiektu delegowanego obiekt delegata jest zwykle przenoszona do innego kodu, który wywoła delegata. Obiekt delegata jest wywoływany przy użyciu nazwy obiektu delegata, a następnie argumentów ujętych w nawiasy, które mają być przekazane do obiektu delegowanego. Poniżej znajduje się przykład wywołania delegata:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Delegat może być wywołany synchronicznie, jak w tym przykładzie lub asynchronicznie przy użyciu `BeginInvoke` metod i. `EndInvoke`  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](../events/index.md)
- [Delegaty](./index.md)

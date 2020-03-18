---
title: Jak deklarować, utworzyć wystąpienia i używać pełnomocnika — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712367"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Jak deklarować, utworzyć wystąpienia i używać delegata (Przewodnik programowania Języka C#)
W języku C# 1.0 i nowszych delegatów można zadeklarować, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C# 2.0 zapewnia prostszy sposób pisania poprzedniej deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 W języku C# 2.0 i nowszych jest również możliwe użycie metody anonimowej do deklarowania i inicjowania [delegata](../../language-reference/builtin-types/reference-types.md), jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 W języku C# 3.0 i nowszych delegatów można również zadeklarować i utworzyć wystąpienia przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład ilustruje deklarowanie, tworzenie wystąpień i korzystanie z pełnomocnika. Klasa `BookDB` hermetyzuje bazę danych księgarni, która prowadzi bazę książek. Udostępnia metodę, `ProcessPaperbackBooks`która znajduje wszystkie książki w kopii zapasowej w bazie danych i wywołuje delegata dla każdego z nich. Typ, `delegate` który jest `ProcessBookDelegate`używany nosi nazwę . Klasa `Test` używa tej klasy do drukowania tytułów i średniej ceny książek w wersji papierowej.  
  
 Użycie delegatów promuje dobre oddzielenie funkcji między bazą danych księgarni a kodem klienta. Kod klienta nie ma wiedzy o tym, jak książki są przechowywane lub jak kod księgarni znajdzie książki w wersji papierowej. Kod księgarni nie ma wiedzy o tym, jakie przetwarzanie jest wykonywane na książkach miękkich po ich znalezieniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Deklarowanie pełnomocnika.  
  
     Następująca instrukcja deklaruje nowy typ delegata.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Każdy typ delegata opisuje liczbę i typy argumentów oraz typ zwracanej wartości metod, które można hermetyzować. Zawsze, gdy potrzebny jest nowy zestaw typów argumentów lub typ wartości zwracanej, należy zadeklarować nowy typ delegata.  
  
- Tworzenie wystąpienia delegata.  
  
     Po zadeklarowaniu typu delegata obiekt delegata musi zostać utworzony i skojarzony z określoną metodą. W poprzednim przykładzie można to zrobić, przekazując `PrintTitle` metodę do `ProcessPaperbackBooks` metody, jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Spowoduje to utworzenie nowego obiektu delegata `Test.PrintTitle`skojarzonego z metodą [statyczną](../../language-reference/keywords/static.md) . Podobnie metoda `AddBookToTotal` niestatyczna na obiekcie `totaller` jest przekazywana jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     W obu przypadkach nowy obiekt delegata `ProcessPaperbackBooks` jest przekazywany do metody.  
  
     Po utworzeniu pełnomocnika metoda, z której jest skojarzona, nigdy się nie zmienia; obiekty delegata są niezmienne.  
  
- Wywoływanie delegata.  
  
     Po utworzeniu obiektu pełnomocnika obiekt delegata jest zazwyczaj przekazywany do innego kodu, który wywoła pełnomocnika. Obiekt delegata jest wywoływana przy użyciu nazwy obiektu delegata, a następnie nawiasy argumenty mają być przekazywane do delegata. Poniżej przedstawiono przykład wywołania delegata:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Delegat może być wywoływany synchronicznie, jak w tym przykładzie, lub `BeginInvoke` `EndInvoke` asynchronicznie za pomocą i metod.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](../events/index.md)
- [Delegaty](./index.md)

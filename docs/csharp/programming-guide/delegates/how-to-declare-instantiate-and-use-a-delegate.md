---
title: 'Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 6c53d7572074db44976494e5eed596bf95aaf456
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858863"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)
W języku C# 1.0 lub nowszy można zadeklarować delegatów, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# w wersji 2.0 zapewnia prostszy sposób zapisu poprzedniej deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 W języku C# w wersji 2.0 lub nowszy, jest również możliwość użycia metodę anonimową do zadeklarowania i zainicjowania [delegować](../../../csharp/language-reference/keywords/delegate.md), jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 W języku C# 3.0 i nowszych delegatów również można zadeklarować i tworzone przy użyciu wyrażenia lambda, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład ilustruje deklarowanie, tworzenie wystąpienia i za pomocą delegata. `BookDB` Klasa hermetyzuje księgarni bazy danych, który obsługuje bazę danych książek. Udostępnia metody, `ProcessPaperbackBooks`, który umożliwia znalezienie wszystkich drukowanego podręcznika książek w bazie danych i wywołuje delegata dla każdego z nich. `delegate` Nosi nazwę typu, który jest używany `ProcessBookDelegate`. `Test` Klasy do drukowania, tytuły i średnia cena drukowanego podręcznika książek, które korzysta z tej klasy.  
  
 Użyj obiektów delegowanych promuje dobre rozdzielanie funkcji między księgarni bazy danych i kod klienta. Kod klienta nie ma informacji o jak książki są przechowywane lub jak kod księgarni znajduje drukowanego podręcznika książki. Kod księgarni nie ma informacji o jakie przetwarzanie jest realizowane na książki drukowanego podręcznika, po nich znajdzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   Deklarowanie delegata.  
  
     Poniższa instrukcja deklaruje nowy typ delegata.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Każdy typ delegata opisuje liczbę i typy argumentów oraz typ wartość zwracaną metody, które można hermetyzacji. Zawsze, gdy będzie potrzebny nowy zestaw typów argumentów lub typ zwracanej wartości, musi być zadeklarowany nowy typ delegata.  
  
-   Utworzenie wystąpienia delegata.  
  
     Po zadeklarowany typ delegata obiektu delegowanego muszą być tworzone i skojarzonych z konkretną metodę. W poprzednim przykładzie, możesz to zrobić, przekazując `PrintTitle` metody `ProcessPaperbackBooks` metodę jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Spowoduje to utworzenie nowego obiektu delegowanego skojarzone z [statyczne](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`. Podobnie, niestatycznej metody `AddBookToTotal` obiektu `totaller` jest przekazywana tak jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     W obu przypadkach nowy obiekt delegowany jest przekazywany do `ProcessPaperbackBooks` metody.  
  
     Po utworzeniu delegata, metoda jest skojarzony z nigdy nie zmiany. Delegat obiekty są niezmienne.  
  
-   Podczas wywoływania delegata.  
  
     Po utworzeniu obiektu delegowanego, obiektu delegowanego jest zazwyczaj przekazywany do innego kodu, który wywoła delegata. Obiekt delegowany jest wywoływany przez przy użyciu nazwy obiektu delegowanego, następuje argumenty ujęty w nawiasy, które zostaną przekazane do delegata. Poniżej znajduje się przykład wywołania delegata:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Delegat może być albo wywoływana synchronicznie, jak w poniższym przykładzie lub asynchronicznie przy użyciu `BeginInvoke` i `EndInvoke` metody.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)

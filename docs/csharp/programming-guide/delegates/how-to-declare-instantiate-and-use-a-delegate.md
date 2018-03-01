---
title: "Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a5329b9e99fcd5830a57eb8f97b4edb67ad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Porady: deklarowanie, tworzenie wystąpień i użycie delegowania (Przewodnik programowania w języku C#)
W języku C# 1.0 lub nowszego oraz delegatów mogą być deklarowane, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 2.0 C# zapewnia prostszy sposób zapisu poprzedniej deklaracji, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 W języku C# 2.0 lub nowszy, jest również możliwe metody anonimowej zadeklarować i zainicjuj [delegować](../../../csharp/language-reference/keywords/delegate.md), jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 W języku C# 3.0 lub nowszego oraz delegatów również można zadeklarować i utworzone za pomocą wyrażenia lambda, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Poniższy przykład przedstawia deklarowanie, tworzenie wystąpień i przy użyciu delegata. `BookDB` Klasa hermetyzuje księgarni bazy danych, który obsługuje bazę danych książek. Udostępnia ona metodę, `ProcessPaperbackBooks`, która wyszukuje wszystkie paperback książki w bazie danych i wywołuje delegata dla każdej z nich. `delegate` Nosi nazwę typu, który jest używany `ProcessBookDelegate`. `Test` Do drukowania tytułów i średniej ceny paperback książek klasa korzysta z tej klasy.  
  
 Używanie delegatów zamienia dobre rozdzielanie funkcji między bazą danych księgarni i kodu klienta. Kod klienta nie ma informacji o przechowywania podręcznikach lub sposób odnajdowania paperback książki w księgarni kodu. Kod księgarni nie ma informacji o jakie przetwarzanie jest realizowane w podręcznikach paperback, po ich znalezienia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   Deklarowanie delegata.  
  
     Następująca instrukcja deklaruje nowy typ obiektu delegowanego.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Każdy typ delegata opisuje liczbę i typy argumentów i typ zwracana wartość metody hermetyzacji przez go. Zawsze, gdy potrzebna jest nowy zestaw typy argumentów lub typ zwracanej wartości, musi być zadeklarowany nowy typ obiektu delegowanego.  
  
-   Tworzenia wystąpienia delegata.  
  
     Po został zadeklarowany typ delegowany, obiektu delegowanego należy utworzyć i skojarzone z określonym — metoda. W poprzednim przykładzie, możesz to zrobić przez przekazanie `PrintTitle` metodę `ProcessPaperbackBooks` metodę jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Spowoduje to utworzenie nowego obiektu delegowanego skojarzone z [statycznych](../../../csharp/language-reference/keywords/static.md) metody `Test.PrintTitle`. Podobnie, Metoda niestatyczna `AddBookToTotal` w obiekcie `totaller` jest przekazywany jak w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     W obu przypadkach nowego obiektu delegowanego jest przekazywany do `ProcessPaperbackBooks` metody.  
  
     Po utworzeniu delegata metoda nie jest skojarzona z nigdy nie zmiany. Delegat obiekty są niezmienne.  
  
-   Wywołanie delegata.  
  
     Po utworzeniu obiektu delegowanego obiektu delegowanego zwykle są przekazywane do innego kodu, który wywoła delegata. Obiektu delegowanego jest wywoływana przy użyciu nazwy obiektu delegowanego, a po niej ujętego w nawiasy argumenty do przekazania do delegata. Poniżej przedstawiono przykładowy wywołania delegata:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Delegat można albo wywołać synchronicznie, jak w poniższym przykładzie lub asynchronicznie za pomocą `BeginInvoke` i `EndInvoke` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)

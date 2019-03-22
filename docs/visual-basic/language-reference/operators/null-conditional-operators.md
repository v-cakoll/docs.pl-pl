---
title: Operatory warunkowe null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348768"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="04d12-102">?.</span><span class="sxs-lookup"><span data-stu-id="04d12-102">?.</span></span> <span data-ttu-id="04d12-103">i? Operatory warunkowe null () (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04d12-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="04d12-104">Sprawdza wartość operandu po lewej stronie w przypadku wartości null (`Nothing`) przed wykonaniem dostęp do elementu członkowskiego (`?.`) lub indeksu (`?()`) operacja; zwraca `Nothing` Jeśli po lewej stronie operand ma wartość `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="04d12-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="04d12-105">Należy pamiętać, że w wyrażeniach, które normalnie zwracane typy wartości, operatorów warunkowych działających z wartością null zwraca <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="04d12-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="04d12-106">Te operatory pomóc w pisaniu mniejszej ilości kodu do obsługi sprawdzanie wartości null, szczególnie w przypadku, gdy malejąco do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="04d12-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="04d12-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="04d12-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="04d12-108">Dla porównania alternatywnych kod dla pierwszego dnia te wyrażenia bez operatorów warunkowych działających z wartością null jest:</span><span class="sxs-lookup"><span data-stu-id="04d12-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="04d12-109">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="04d12-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="04d12-110">Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca `Nothing`, pozostała część zatrzymuje wykonywanie łańcucha.</span><span class="sxs-lookup"><span data-stu-id="04d12-110">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="04d12-111">W poniższym przykładzie `C(E)` nie jest oceniany, jeśli `A`, `B`, lub `C` daje w wyniku `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="04d12-111">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="04d12-112">Innym zastosowaniem uzyskać dostęp do elementu członkowskiego warunkowe null jest wywoływać delegatów w sposób wątkowo ze znacznie mniejszej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="04d12-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="04d12-113">W poniższym przykładzie zdefiniowano dwa typy `NewsBroadcaster` i `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="04d12-113">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="04d12-114">Elementy wiadomości są wysyłane do odbiorcy przez `NewsBroadcaster.SendNews` delegować.</span><span class="sxs-lookup"><span data-stu-id="04d12-114">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="04d12-115">Jeśli nie ma elementów w `SendNews` listy wywołań `SendNews` delegować zgłasza <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="04d12-115">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="04d12-116">Przed operatory warunkowe null, kod tak, jak zapewnić następujące listy wywołanie delegata nie była `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="04d12-116">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="04d12-117">Nowy sposób jest znacznie prostszy:</span><span class="sxs-lookup"><span data-stu-id="04d12-117">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="04d12-118">Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `SendNews` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="04d12-118">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="04d12-119">Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `SendNews?(String)` do wywołania delegata przy użyciu operatora warunkowego „null”.</span><span class="sxs-lookup"><span data-stu-id="04d12-119">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="04d12-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04d12-120">See also</span></span>

- [<span data-ttu-id="04d12-121">Operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04d12-121">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="04d12-122">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04d12-122">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="04d12-123">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04d12-123">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)

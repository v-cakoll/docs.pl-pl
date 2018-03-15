---
title: "Używanie indeksatorów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 17bbfabe8a53fc51e81434d0a2bd9fb2b29c4695
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="using-indexers-c-programming-guide"></a>Używanie indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są składni wygody, które umożliwiają tworzenie [klasy](../../../csharp/language-reference/keywords/class.md), [struktury](../../../csharp/language-reference/keywords/struct.md), lub [interfejsu](../../../csharp/language-reference/keywords/interface.md) że aplikacje klienckie mogą uzyskać dostęp, podobnie jak tablicy. Indeksatory najczęściej są implementowane w typach, których podstawowym celem jest hermetyzować wewnętrznej kolekcji lub tablicy. Na przykład załóżmy, że istnieje klasa o nazwie TempRecord reprezentujący temperatury w Farenheit zarejestrowane w różnym czasie 10 w okresie 24 godzin. Klasa zawiera tablicę o nazwie "temps" typ float do reprezentowania temperatury, a <xref:System.DateTime> reprezentujący datę temperatury zostały zarejestrowane. Implementując indeksatora w tej klasie, klienci mogą uzyskiwać dostęp temperatur w wystąpieniu TempRecord jako `float temp = tr[4]` zamiast jako `float temp = tr.temps[4]`. Notacja indeksatora nie tylko ułatwia składnia dla aplikacji klienckich; zapewnia także klasy i jej celem bardziej intuicyjne innych deweloperom zrozumieć.  
  
 Aby zadeklarować indeksatora w klasie lub strukturze, należy użyć [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe, jak w poniższym przykładzie:  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Typ indeksatora i typ jego parametrów muszą być co najmniej jako dostępne jako indeksatora samej siebie. Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Aby uzyskać więcej informacji o tym, jak korzystać z indeksatorów przy użyciu interfejsu, zobacz [indeksatory interfejsu](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 Podpis indeksatora składa się z liczbę i typy parametrów formalnych. Nie ma typu indeksatora lub nazwy parametrów formalnych. W przypadku więcej niż jeden indeksator w tej samej klasie, muszą mieć różne sygnatury.  
  
 Wartość indeksator nie jest sklasyfikowany jako zmienną; w związku z tym nie można przekazać wartości indeksatora jako [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru.  
  
 Aby dostarczyć indeksatora z nazwą innych języków można użyć, użyj `name` atrybutu w deklaracji. Na przykład:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Ten indeksator będzie mieć nazwę `TheItem`. Nie udostępniasz atrybut name spowodowałoby `Item` nazwę domyślną.  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia sposób zadeklarować pola tablicy prywatnej, `temps`i indeksatora. Indeksator umożliwia bezpośredni dostęp do wystąpienia `tempRecord[i]`. Alternatywa dla użycia indeksator ma deklarować tablic jako [publicznego](../../../csharp/language-reference/keywords/public.md) elementu członkowskiego i dostęp do jego elementów członkowskich `tempRecord.temps[i]`, bezpośrednio.  
  
 Zwróć uwagę, że dostęp indeksatora jest sprawdzane, na przykład w `Console.Write` instrukcji, [uzyskać](../../../csharp/language-reference/keywords/get.md) wywoływana jest metoda dostępu. W związku z tym jeśli nie `get` akcesor istnieje, występuje błąd kompilacji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indeksowania, używając innych wartości  
 C# nie ogranicza typ indeksu do liczby całkowitej. Na przykład może być przydatne do używania ciągu z indeksatora. Takie indeksatora może być implementowana przez wyszukiwania ciągów w kolekcji i zwracanie odpowiednią wartość. Jak można przeciążać metod dostępu, wersje string i integer mogą współistnieć.  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 W tym przykładzie klasa jest zadeklarowana, który przechowuje dni tygodnia. A `get` metody dostępu jest zadeklarowany jako ciąg znaków, dzień i zwraca odpowiednie liczby całkowitej. Na przykład niedziela będzie zwraca 0, poniedziałek zostanie zwrócona wartość 1 itd.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Istnieją dwa sposoby głównego, w których można zwiększyć bezpieczeństwo i niezawodność indeksatory:  
  
-   Pamiętaj dołączyć do nich pewien rodzaj strategii obsługi błędów do obsługi szansy kodu klienta, przekazując wartość nieprawidłowy indeks. W pierwszym przykładzie we wcześniejszej części tego tematu klasa TempRecord udostępnia właściwości Length, który umożliwia kod klienta, aby zweryfikować dane wejściowe przed przekazaniem go do indeksatora. Można również wprowadzić obsługi kodu wewnątrz samego indeksatora błędów. Pamiętaj dokumentów dla użytkowników wszelkie wyjątki, które zgłaszają wewnątrz metody dostępu indeksatora.  
  
-   Ustaw dostępności `get` i [ustawić](../../../csharp/language-reference/keywords/set.md) metody dostępu należy stosować jak największe restrykcje jest uzasadnione. Jest to ważne w przypadku `set` dostępu w szczególności. Aby uzyskać więcej informacji, zobacz [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)

---
title: Konwertowanie między ciągami a innymi typami danych
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ae8f7c2159191536013fafd8bfd10fb9a93fb785
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394224"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="e37ec-102">Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e37ec-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="e37ec-103">Można przekonwertować wartość liczbową, `Boolean` lub datę/godzinę na `String` .</span><span class="sxs-lookup"><span data-stu-id="e37ec-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="e37ec-104">Możesz również skonwertować w odwrotnym kierunku — od wartości ciągu na wartość numeryczną, `Boolean` lub `Date` — pod warunkiem, że zawartość ciągu może być interpretowana jako prawidłowa wartość docelowego typu danych.</span><span class="sxs-lookup"><span data-stu-id="e37ec-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="e37ec-105">Jeśli nie, wystąpi błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e37ec-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="e37ec-106">Konwersje dla wszystkich tych przypisań, w obu kierunkach, zawężają konwersje.</span><span class="sxs-lookup"><span data-stu-id="e37ec-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="e37ec-107">Należy użyć słów kluczowych konwersji typu (,,,,,,,,, `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` ,,,,, `CStr` `CUInt` `CULng` `CUShort` i `CType` ).</span><span class="sxs-lookup"><span data-stu-id="e37ec-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="e37ec-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>Funkcje i <xref:Microsoft.VisualBasic.Conversion.Val%2A> zapewniają dodatkową kontrolę nad konwersjami między ciągami i liczbami.</span><span class="sxs-lookup"><span data-stu-id="e37ec-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="e37ec-109">Jeśli zdefiniowano klasę lub strukturę, można zdefiniować operatory konwersji typów między `String` i typem klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e37ec-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="e37ec-110">Aby uzyskać więcej informacji, zobacz [jak: definiowanie operatora konwersji](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e37ec-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="e37ec-111">Konwersja liczb na ciągi</span><span class="sxs-lookup"><span data-stu-id="e37ec-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="e37ec-112">Możesz użyć funkcji, `Format` Aby skonwertować liczbę do sformatowanego ciągu, który może zawierać nie tylko odpowiednie cyfry, ale także formatowanie symboli, takich jak znak waluty (na przykład `$` ), separatory tysięcy lub *symbole grupowania cyfr* (takie jak `,` ), oraz separator dziesiętny (na przykład `.` ).</span><span class="sxs-lookup"><span data-stu-id="e37ec-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="e37ec-113">`Format`Program automatycznie używa odpowiednich symboli zgodnie z ustawieniami **opcji regionalnych** określonymi w **Panelu sterowania**systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e37ec-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="e37ec-114">Należy zauważyć, że operator łączenia ( `&` ) może przekonwertować liczbę na ciąg niejawnie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e37ec-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="e37ec-115">Konwersja ciągów na liczby</span><span class="sxs-lookup"><span data-stu-id="e37ec-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="e37ec-116">Możesz użyć funkcji, `Val` Aby jawnie skonwertować cyfry w ciągu na liczbę.</span><span class="sxs-lookup"><span data-stu-id="e37ec-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="e37ec-117">`Val`odczytuje ciąg, dopóki nie napotka znaku innego niż cyfra, spacja, tabulator, wysuw wiersza lub kropki.</span><span class="sxs-lookup"><span data-stu-id="e37ec-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="e37ec-118">Sekwencje "&O" i "&H" zmieniają podstawę systemu liczb i przerywają skanowanie.</span><span class="sxs-lookup"><span data-stu-id="e37ec-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="e37ec-119">Dopóki nie zakończy się odczytywanie, program `Val` konwertuje wszystkie odpowiednie znaki na wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="e37ec-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="e37ec-120">Na przykład poniższa instrukcja zwraca wartość `141.825` .</span><span class="sxs-lookup"><span data-stu-id="e37ec-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="e37ec-121">Gdy Visual Basic konwertuje ciąg na wartość liczbową, używa ustawień **opcji regionalnych** określonych w **Panelu sterowania** systemu Windows, aby interpretować separator tysięcy, separator dziesiętny i symbol waluty.</span><span class="sxs-lookup"><span data-stu-id="e37ec-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="e37ec-122">Oznacza to, że konwersja może się powieść w ramach jednego ustawienia, ale nie do innego.</span><span class="sxs-lookup"><span data-stu-id="e37ec-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="e37ec-123">Na przykład `"$14.20"` jest akceptowalny w ustawieniach regionalnych (Stany Zjednoczone) w języku angielskim, ale nie w ustawieniach regionalnych.</span><span class="sxs-lookup"><span data-stu-id="e37ec-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37ec-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e37ec-124">See also</span></span>

- [<span data-ttu-id="e37ec-125">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e37ec-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="e37ec-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="e37ec-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e37ec-127">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="e37ec-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e37ec-128">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e37ec-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="e37ec-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="e37ec-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="e37ec-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e37ec-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="e37ec-131">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e37ec-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e37ec-132">Opracowywanie aplikacji globalnych i zlokalizowanych</span><span class="sxs-lookup"><span data-stu-id="e37ec-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

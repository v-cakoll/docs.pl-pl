---
title: Object — typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 94d3ddcf71194eb69a2d26bcdf549aaf693e46e6
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255709"
---
# <a name="object-data-type"></a>Object — typ danych
Zawiera adresy, które odwołują się do obiektów. Dowolnego typu odwołania (ciąg, macierz, klasy lub interfejsu) można przypisać do `Object` zmiennej. `Object` Zmiennej może również odnosić się do danych o dowolnym typie wartości (numeryczne, `Boolean`, `Char`, `Date`, struktury lub wyliczenia).  
  
## <a name="remarks"></a>Uwagi  
 `Object` Danych dowolnego typu danych, w tym dowolne wystąpienie obiektu, aplikacja rozpoznaje wskazać typ danych. Użyj `Object` Jeśli nie wiesz, w czasie kompilacji dane typu zmiennej może wskazywać.  
  
 Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).  
  
## <a name="data-types"></a>Typy danych  
 Można przypisać zmiennej, stałej lub wyrażenia dowolnego typu danych, aby `Object` zmiennej. Można ustalić typu danych `Object` obecnie odnosi się zmienna, możesz użyć <xref:System.Type.GetTypeCode%2A> metody <xref:System.Type?displayProperty=nameWithType> klasy. Ilustruje to poniższy przykład.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` — Typ danych jest typem referencyjnym. Jednakże, Visual Basic traktuje `Object` zmienną jako typ wartości, gdy jest on odnosi się do danych o typie wartości.  
  
## <a name="storage"></a>Magazyn  
 Niezależnie od typu danych, to dotyczy, `Object` automatycznie, ale raczej wskaźnika do wartości zmiennej nie zawiera wartości danych. Zawsze używa cztery bajty w pamięci komputera, ale nie obejmuje to magazyn dla danych reprezentujący wartość zmiennej. Ze względu na kod, który używa wskaźnika do zlokalizowania danych `Object` zawierający typy wartości zmiennych są nieco wolniejszy dostęp niż jawnie wpisane zmienne do.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać o tym, że typy wskaźników w innych środowiskach nie są zgodne z języka Visual Basic `Object` typu.  
  
-   **Wydajność.** Zmienna deklarowana za pomocą `Object` typu jest na tyle elastyczna, aby zawierała odwołanie do dowolnego obiektu. Jednak gdy wywołujesz metodę lub właściwość takiej zmiennej zawsze wiąże się z *późnym wiązaniu* (w czasie wykonywania). Aby wymusić *wczesne powiązania* (w czasie kompilacji) i większą wydajność, Zadeklaruj zmienną o nazwie określonej klasy lub go rzutować na typ danych określonych.  
  
     Kiedy Deklarujesz zmienną obiektu, spróbuj użyć typu określonej klasy, na przykład <xref:System.OperatingSystem>, zamiast ogólnych `Object` typu. Należy również użyć najbardziej odpowiednią klasę dostępne, takich jak <xref:System.Windows.Forms.TextBox> zamiast <xref:System.Windows.Forms.Control>, dzięki czemu można uzyskać dostęp, jego właściwości i metod. Zazwyczaj można używać **klasy** listy w **przeglądarki obiektów** można znaleźć nazwy dostępnych klas.  
  
-   **Rozszerzanie.** Wszystkie typy danych i wszystkie typy referencyjne mogą zostać poszerzone do `Object` typu danych. Oznacza to, że można przekonwertować dowolnego typu do `Object` nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
     Jednak po konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje o nazwie *pakowania* i *Rozpakowywanie*, udostępniają wykonywania wolniej.  
  
-   **Znaki typu.** `Object` nie ma znak literalny typu lub znak typu identyfikator.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.Object?displayProperty=nameWithType> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `Object` zmiennej wskazuje na wystąpienie obiektu.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Instrukcje: określanie, czy dwa obiekty są powiązane](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Instrukcje: określanie, czy dwa obiekty są jednakowe](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

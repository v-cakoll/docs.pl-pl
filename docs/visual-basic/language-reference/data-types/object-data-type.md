---
title: "Object — typ danych"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 847f2b50296ad1a1ba6f0009d1d6afced27f9abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-data-type"></a>Object — typ danych
Przechowuje adresy, które odwołują się do obiektów. Można przypisać do dowolnego typu odwołanie (ciąg, tablic, klasy lub interfejsu) `Object` zmiennej. `Object` Zmiennej znajdują się dane dowolnego typu wartość (numeryczną, `Boolean`, `Char`, `Date`, struktury lub wyliczenia).  
  
## <a name="remarks"></a>Uwagi  
 `Object` Danych dowolnego typu danych, w tym wszystkie wystąpienia obiektu aplikacja rozpoznaje może wskazywać typ danych. Użyj `Object` Jeśli nie znasz w czasie kompilacji, jakie dane typu zmienną może wskazywać.  
  
 Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).  
  
## <a name="data-types"></a>Typy danych  
 Można przypisać zmiennej, stałej lub wyrażenia typu danych do `Object` zmiennej. Można ustalić typu danych `Object` obecnie odnosi się zmienna, możesz użyć <xref:System.Type.GetTypeCode%2A> metody <xref:System.Type?displayProperty=nameWithType> klasy. Ilustruje to poniższy przykład.  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` — Typ danych jest typem referencyjnym. Jednak traktuje Visual Basic `Object` zmiennej jako typ wartości, gdy odwołuje się do danych typu wartości.  
  
## <a name="storage"></a>Magazyn  
 Niezależnie od typu danych odwołuje się do, `Object` zmiennej nie zawiera wartości danych sam, ale raczej wskaźnik do wartości. Zawsze używa czterech bajtów pamięci, ale nie obejmuje magazyn danych reprezentujący wartość zmiennej. Ze względu na kod, który używa wskaźnika do lokalizowania danych `Object` zawierający typy wartości zmiennych są nieco dłużej dostępu niż jawnie zmienne typu.  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typów wskaźnikowych w innych środowiskach nie są zgodne z programem Visual Basic `Object` typu.  
  
-   **Wydajność.** Zmienna zadeklarowana z `Object` typ jest wystarczająco elastyczny, aby zawierać odwołania do dowolnego obiektu. Jednak po wywołaniu metody lub właściwości na przekazanie zmiennej, należy zawsze pociągnąć za sobą *późne wiązanie* (w czasie wykonywania). Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepsza wydajność, zadeklarować zmiennej o nazwie określonej klasy lub rzutować go na typ danych.  
  
     Deklaracja zmiennej obiektu, spróbuj użyć określonego typu klasy, na przykład <xref:System.OperatingSystem>, zamiast ogólnych `Object` typu. Należy korzystać z najbardziej określonej klasy dostępne, takich jak <xref:System.Windows.Forms.TextBox> zamiast <xref:System.Windows.Forms.Control>, dzięki czemu można uzyskać dostępu do jego właściwości i metody. Zazwyczaj można używać **klasy** na liście **przeglądarki obiektów** można znaleźć nazwy klasy dostępne.  
  
-   **Rozszerzanie.** Wszystkie typy danych i wszystkie typy referencyjne rozszerzane `Object` — typ danych. Oznacza to, że można przekonwertować dowolnego typu do `Object` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
     Jednak po konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje o nazwie *boxing* i *rozpakowującej*, udostępniają wykonywania wolniej.  
  
-   **Znaki typu.** `Object`nie ma znak literalny typu ani znak typu identyfikator.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Object?displayProperty=nameWithType> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia `Object` zmiennej wskazuje na wystąpienie obiektu.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Porady: Określanie, czy dwa obiekty są powiązane](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Porady: Określanie, czy dwa obiekty są identyczne](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

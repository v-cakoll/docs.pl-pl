---
title: <inheritdoc> — C# Przewodnik programowania
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795162"
---
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc > (C# Przewodnik programowania)

## <a name="syntax"></a>Składnia  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a>InheritDoc

Dziedzicz Komentarze XML z klas bazowych, interfejsów i podobnych metod. Eliminuje to niechciane kopiowanie i wklejanie zduplikowanych komentarzy XML i automatycznie synchronizuje komentarze XML. 
  
## <a name="remarks"></a>Uwagi  
Dodaj komentarze XML do klas bazowych lub interfejsów i pozwól InheritDoc skopiować komentarze do implementacji klas.

Dodaj komentarze XML do metod synchronicznych i pozwól InheritDoc skopiować komentarze do Twoich asynchronicznych wersji tych samych metod.  

Jeśli chcesz skopiować komentarze z określonego elementu członkowskiego, możesz użyć atrybutu `cref`, aby określić element członkowski.
  
## <a name="examples"></a>Przykłady
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

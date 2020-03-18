---
title: <inheritdoc>- Przewodnik programowania C#
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156951"
---
# <a name="inheritdoc-c-programming-guide"></a>\<> (Przewodnik programowania C#)

## <a name="syntax"></a>Składnia  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

Dziedzicz komentarze XML z klas podstawowych, interfejsów i podobnych metod. Eliminuje to niepożądane kopiowanie i wklejanie zduplikowanych komentarzy XML i automatycznie synchronizuje komentarze XML.
  
## <a name="remarks"></a>Uwagi  
Dodaj komentarze XML w klasach podstawowych lub interfejsach i pozwól InheritDoc skopiować komentarze do klasy implementującej.

Dodaj komentarze XML do metod synchronicznych i pozwól InheritDoc skopiować komentarze do asynchronicznych wersji tych samych metod.  

Jeśli chcesz skopiować komentarze od określonego członka, `cref` możesz użyć atrybutu, aby określić element członkowski.
  
## <a name="examples"></a>Przykłady
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zalecane tagi do komentarzy do dokumentacji](./recommended-tags-for-documentation-comments.md)

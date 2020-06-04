---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 42f40581d252956433165789d6674234a295867c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400149"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)
Określa przykład dla elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Opis przykładu kodu.  
  
## <a name="remarks"></a>Uwagi  
 `<example>`Tag pozwala określić przykład użycia metody lub innego elementu członkowskiego biblioteki. Zwykle obejmuje to użycie [\<code>](code.md) znacznika.  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<example>` znacznika, aby dołączyć przykład do użycia `ID` pola.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)

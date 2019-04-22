---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 16d10b2f955a4d9a02075ee4cc40dfa2b18c3541
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814513"
---
# <a name="para-visual-basic"></a>\<para > (Visual Basic)
Określa, że zawartość jest w formacie akapitu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Tekst akapitu.  
  
## <a name="remarks"></a>Uwagi  
 `<para>` Tag jest przeznaczona do użytku wewnątrz znacznik, taki jak [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [ \<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodawanie struktury w tekście.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<para>` tagu podziału sekcję Spostrzeżenia, aby `UpdateRecord` metody do dwóch akapitach.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

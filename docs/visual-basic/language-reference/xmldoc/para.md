---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352302"
---
# <a name="para-visual-basic"></a>\<para > (Visual Basic)
Określa, że zawartość jest sformatowana w akapicie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Tekst akapitu.  
  
## <a name="remarks"></a>Uwagi  
 Tag `<para>` jest używany wewnątrz tagu, takiego jak [\<podsumowanie >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [\<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodanie struktury do tekstu.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<para>`, aby podzielić sekcję Uwagi dla metody `UpdateRecord` na dwa akapity.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

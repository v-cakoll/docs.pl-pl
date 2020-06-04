---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400076"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
Określa, że zawartość jest sformatowana w akapicie.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Parametry  
 `content`  
 Tekst akapitu.  
  
## <a name="remarks"></a>Uwagi  
 `<para>`Tag jest używany wewnątrz tagu, takiego jak [\<summary>](summary.md) , [\<remarks>](remarks.md) , lub [\<returns>](returns.md) , i umożliwia dodanie struktury do tekstu.  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `<para>` znacznika, aby podzielić sekcję Uwagi dla `UpdateRecord` metody na dwa akapity.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)

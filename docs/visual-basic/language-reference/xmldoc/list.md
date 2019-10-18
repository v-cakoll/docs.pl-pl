---
title: <list> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524751"
---
# <a name="list-visual-basic"></a>> \<list (Visual Basic)
Definiuje listę lub tabelę.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 Typ listy. Musi być "punktorem" dla listy punktowanej, "number" dla listy numerowanej lub "Table" dla jednokolumnowej tabeli.  
  
 `term`  
 Używane tylko wtedy, gdy `type` jest "Table". Termin do zdefiniowania, który jest zdefiniowany w tagu Description.  
  
 `description`  
 Gdy `type` jest "punktor" lub "number", `description` jest pozycją na liście, gdy `type` jest "Tabela", `description` jest definicją `term`.  
  
## <a name="remarks"></a>Uwagi  
 Blok `<listheader>` definiuje nagłówek tabeli lub listy definicji. Podczas definiowania tabeli należy tylko podać wpis dla `term` w nagłówku.  
  
 Każdy element na liście jest określany za pomocą bloku `<item>`. Podczas tworzenia listy definicji należy określić zarówno `term`, jak i `description`. Jednak w przypadku tabeli, listy punktowanej lub listy numerowanej trzeba podać tylko wpis dla `description`.  
  
 Lista lub tabela może zawierać dowolną liczbę bloków `<item>` w zależności od potrzeb.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<list>`, aby zdefiniować listę punktowaną w sekcji uwagi.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

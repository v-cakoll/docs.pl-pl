---
title: <list>
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
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400089"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
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
 Gdy `type` ma wartość "Bullet" lub "number", `description` to element na liście, gdy `type` jest "Tabela", `description` jest definicją `term` .  
  
## <a name="remarks"></a>Uwagi  
 `<listheader>`Blok definiuje nagłówek tabeli lub listy definicji. Podczas definiowania tabeli należy tylko podać wpis `term` w nagłówku.  
  
 Każdy element na liście jest określony za pomocą `<item>` bloku. Podczas tworzenia listy definicji należy określić zarówno, `term` jak i `description` . Jednak w przypadku tabeli, listy punktowanej lub listy numerowanej wystarczy podać wpis dla `description` .  
  
 Lista lub tabela może zawierać tyle `<item>` bloków, ile jest to konieczne.  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `<list>` znacznika do definiowania listy punktowanej w sekcji uwagi.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)

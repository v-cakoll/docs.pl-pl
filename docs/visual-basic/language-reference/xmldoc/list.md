---
title: '&lt;Lista&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a>&lt;Lista&gt; (Visual Basic)
Definiuje listy lub tabeli.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ listy. Musi być "bullet" do listy punktowanej, "numer" Lista numerowana lub "Tabela" dla tabeli dwie kolumny.  
  
 `term`  
 Używana tylko w przypadku `type` jest "table". Termin Aby zdefiniować, który jest zdefiniowany w tagu opis.  
  
 `description`  
 Gdy `type` "bullet" lub "number" `description` jest pozycją na liście po `type` jest "tabeli" `description` znajduje się definicja metody `term`.  
  
## <a name="remarks"></a>Uwagi  
 `<listheader>` Bloku definiuje nagłówek tabeli lub definicji listy. Podczas definiowania tabeli, wystarczy podać wpis dotyczący `term` w nagłówku.  
  
 Każdy element na liście zostanie określony z `<item>` bloku. Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`. Jednak dla tabeli, lista punktowana lub Lista numerowana, wystarczy podać wpis dotyczący `description`.  
  
 Listy lub tabeli może mieć tyle `<item>` blokuje zgodnie z potrzebami.  
  
 Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<list>` tag do definiowania listy punktowanej w sekcji uwag.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

---
title: '&lt;Lista&gt; (Visual Basic)'
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
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603616"
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

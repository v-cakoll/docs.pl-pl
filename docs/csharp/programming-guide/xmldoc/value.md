---
title: '&lt;wartość&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 24ef4aba13668cd04e20f17ebffac9eb68e796ca
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561631"
---
# <a name="ltvaluegt-c-programming-guide"></a>&lt;wartość&gt; (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 \<Wartość > znacznik umożliwia opisują wartość, która reprezentuje właściwość. Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodów w środowisku programowania Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag w przypadku nowej właściwości. Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

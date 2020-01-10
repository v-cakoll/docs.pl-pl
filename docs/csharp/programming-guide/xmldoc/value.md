---
title: <value> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: a30435c40ad31e026b9cb1952086984548f0cdb6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694546"
---
# <a name="value-c-programming-guide"></a>> wartości \<(C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Tag \<wartość > umożliwia opisanie wartości reprezentowanej przez właściwość. Należy pamiętać, że po dodaniu właściwości za pośrednictwem Kreatora kodu w środowisku deweloperskim Visual Studio .NET zostanie dodany tag [\<summary >](./summary.md) dla nowej właściwości. Następnie należy ręcznie dodać tag \<wartość >, aby opisać wartość, którą reprezentuje właściwość.  
  
 Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

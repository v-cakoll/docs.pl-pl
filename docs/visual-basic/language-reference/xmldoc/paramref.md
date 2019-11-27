---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 78227a17584271f91283198e95f5aa389b3ef14b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352279"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
Formatuje słowo jako parametr.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru, do którego się odwołuje. Ujmij nazwę w znaki podwójnego cudzysłowu ("").  
  
## <a name="remarks"></a>Uwagi  
 Tag `<paramref>` umożliwia wskazanie, że słowo jest parametrem. Plik XML można przetworzyć, aby sformatować ten parametr w dowolny sposób.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<paramref>`, aby odwołać się do parametru `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

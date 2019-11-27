---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346959"
---
# <a name="exception-visual-basic"></a>> \<wyjątków (Visual Basic)
Określa, które wyjątki mogą być zgłaszane.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML. `member` musi znajdować się w podwójnym cudzysłowie ("").  
  
 `description`  
 Opis.  
  
## <a name="remarks"></a>Uwagi  
 Użyj znacznika `<exception>`, aby określić, które wyjątki mogą być zgłaszane. Ten tag jest stosowany do definicji metody.  
  
 Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa znacznika `<exception>`, aby opisać wyjątek, który może zgłosić funkcja `IntDivide`.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

---
title: <exception> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 639e3a345fc8ed3d348461718f73ead6167158db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675926"
---
# <a name="exception-c-programming-guide"></a>\<wyjątek > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametry  
 cref = " `member`"  
 Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML. `member` musi znajdować się w znaki podwójnego cudzysłowu ("").  
  
 Aby uzyskać więcej informacji na temat formatowania `member` Aby odwołać się do ogólnego typu, zobacz [przetwarzanie pliku XML](processing-the-xml-file.md).
  
 `description`  
 Opis wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 \<Wyjątku > należy określić, które wyjątki mogą zostać wygenerowane. Ten tag można zastosować do definicji dla metody, właściwości, zdarzeń i indeksatorów.  
  
 Kompiluj przy użyciu [/doc](../../language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
 Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątków i wyjątków](../exceptions/index.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](recommended-tags-for-documentation-comments.md)

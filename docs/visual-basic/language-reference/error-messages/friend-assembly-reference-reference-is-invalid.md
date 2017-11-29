---
title: "Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy
Odwołanie do przyjaznego zestawu \<odwołania > jest nieprawidłowy. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ klucz publiczny zestawu o silnej nazwie friend. Dołącz klucz publiczny, jako część nazwy zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu przy użyciu `PublicKey` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.AssemblyName>  
 [Przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [Porady: tworzenie oznaczonych przyjaznych zestawów](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)

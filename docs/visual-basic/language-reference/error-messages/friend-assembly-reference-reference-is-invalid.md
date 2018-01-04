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
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Odwołanie do przyjaznego zestawu &lt;odwołania&gt; jest nieprawidłowy
Odwołanie do przyjaznego zestawu \<odwołania > jest nieprawidłowy. Zestawy podpisane silnymi nazwami muszą określać klucz publiczny w swoich deklaracjach InternalsVisibleTo.  
  
 Nazwa zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu identyfikuje zestawu z silną nazwą, ale nie obejmuje `PublicKey` atrybutu.  
  
 **Identyfikator błędu:** BC31535  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ klucz publiczny zestawu o silnej nazwie friend. Dołącz klucz publiczny, jako część nazwy zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Konstruktor atrybutu przy użyciu `PublicKey` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.AssemblyName>  
 [Przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 


---
title: "Tworzenie atrybutów niestandardowych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a24553ae4cc2186e805d76ddb37f38c0322aeac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-visual-basic"></a>Tworzenie atrybutów niestandardowych (Visual Basic)
Można utworzyć własne niestandardowe atrybuty, definiując klasę atrybutów klasy, która jest pochodną bezpośrednio lub pośrednio <xref:System.Attribute>, która sprawia, że identyfikacji definicje atrybutów w metadanych szybkie i łatwe. Załóżmy, że chcesz typów tagu o nazwie programisty autorze typu. Możesz zdefiniować niestandardowy `Author` klasy atrybutu:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 Nazwa klasy jest nazwa atrybutu `Author`. Jest pochodną `System.Attribute`, co klasa atrybutu niestandardowego. Konstruktor parametry są parametry pozycyjne atrybutu niestandardowego. W tym przykładzie `name` jest parametrów pozycyjnych. Parametry są nazwane właściwości lub pola publiczne odczytu i zapisu. W takim przypadku `version` tylko nosi nazwę parametru. Zwróć uwagę na użycie `AttributeUsage` atrybutu, aby `Author` atrybut jest prawidłowy tylko w klasie i `Structure` deklaracji.  
  
 Ten nowy atrybut można użyć w następujący sposób:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`Nazwany parametr `AllowMultiple`, z której można utworzyć atrybutu niestandardowego, jednorazowych lub multiuse. W poniższym przykładzie jest tworzony multiuse atrybutu.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 W poniższym przykładzie kodu wiele atrybutów tego samego typu są stosowane do klasy.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  Jeśli atrybut klasy zawiera właściwości, tej właściwości musi być do odczytu / zapisu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection>  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Wpisywanie atrybutów niestandardowych](../../../../standard/attributes/writing-custom-attributes.md)  
 [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)

---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a>/langversion (Visual Basic)
Powoduje, że kompilator, aby zaakceptować tylko składni, który znajduje się w określonej wersji języka Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a>Argumenty  
 `version`  
 Wymagany. Wersja językowa mają być użyte podczas kompilacji. Akceptowane wartości to `9`, `9.0`, `10`, i `10.0`.  
  
## <a name="remarks"></a>Uwagi  
 `/langversion` Opcja określa, jakie składni akceptuje kompilatora. Na przykład możesz określić, że wersja językowa jest 9.0, kompilator generuje błędy składni, który jest prawidłowy tylko w wersji 10.0 lub nowszej.  
  
 Podczas tworzenia aplikacji, że docelowy różne wersje programu .NET Framework, można użyć tej opcji. Na przykład jeśli ma być przeznaczona dla programu .NET Framework 3.5, można tę opcję, aby upewnić się, że nie należy używać składni języka w wersji 10.0.  
  
 Można ustawić `/langversion` bezpośrednio tylko przy użyciu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `sample.vb` 9.0 Visual Basic.  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Przeznaczonych dla określonej wersji platformy .NET](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)

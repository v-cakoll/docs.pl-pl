---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
Tworzy łącze do zasobów zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagany. Plik zasobu, aby utworzyć łącze do zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").  
  
 `identifier`  
 Opcjonalny. Nazwa logiczna zasobu. Nazwa, która jest używana do załadowania zasobu. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publicznych lub prywatnych w manifeście zestawu, na przykład: `/linkres:filename.res,myname.res,public`. Domyślnie `filename` jest publiczny w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 `/linkresource` Opcja nie jest możliwe osadzanie pliku zasobów w pliku wyjściowym; użyj `/resource` opcję, aby to zrobić.  
  
 `/linkresource` Opcja wymaga jednego z `/target` opcje inne niż `/target:module`.  
  
 Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw. (Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Aby uzyskać dostęp do innych zasobów w czasie wykonywania, należy użyć metody, które zaczynają się od `GetManifestResource` w <xref:System.Reflection.Assembly> klasy.  
  
 Nazwa pliku może być dowolnym formacie pliku. Na przykład można ustawić natywnej biblioteki DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej zestawów i dostępne z kodu zarządzanego w zestawie.  
  
 Krótka forma z `/linkresource` jest `/linkres`.  
  
> [!NOTE]
>  `/linkresource` Opcja nie jest dostępny w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i łącza do pliku zasobów `Rf.resource`.  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /win32resource
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d839b1100b1ae76fbd4653ebc60c79db11b77685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="win32resource"></a>/win32resource
Wstawia plik zasobów Win32 w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku zasobu, aby dodać do pliku wyjściowego. Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Można utworzyć pliku zasobów Win32 z kompilatora zasobów systemu Windows (RC) firmy Microsoft.  
  
 Zasób Win32 może zawierać wersji lub mapy bitowej (ikona) informacje, które pomogą zidentyfikować aplikację w **Eksploratora plików**. Jeśli nie określisz `/win32resource`, kompilator generuje informacje o wersji, w zależności od używanej wersji zestawu. `/win32resource` i `/win32icon` wykluczają się wzajemnie.  
  
 Zobacz [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu lub [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu.  
  
> [!NOTE]
>  `/win32resource` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik zasobów Win32 `Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65149c617220966bc3bb6897d757a71cd60167d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon"></a>/win32icon
Wstawia plik .ico w pliku wyjściowym. Ten plik .ico reprezentuje plik wyjściowy w **Eksploratora plików**.  
  
## <a name="syntax"></a>Składnia  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Plik .ico, aby dodać do pliku wyjściowego. Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Można utworzyć plik .ico z kompilatora zasobów systemu Windows (RC) firmy Microsoft. Kompilator zasobów jest wywoływane, gdy kompilacja programu Visual C++; plik .rc jest utworzony plik .ico. `/win32icon` i `/win32resource` wykluczają się wzajemnie.  
  
 Zobacz [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu lub [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu. Zobacz [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować pliku .res.  
  
|Aby ustawić/win32icon w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **ikona** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik .ico `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a>/sdkpath
Określa lokalizację pliku Mscorlib.dll i pliku Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Składnia  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Katalog zawierający wersje Mscorlib.dll i pliku Microsoft.VisualBasic.dll do użycia podczas kompilacji. Ta ścieżka nie została zweryfikowana, dopóki nie został załadowany. Nazwę katalogu należy ująć w cudzysłów ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja nakazuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora, aby załadować Mscorlib.dll i pliku Microsoft.VisualBasic.dll pliki z lokalizacji innych niż domyślne. `/sdkpath` Opcja został zaprojektowany do użytku z [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). [!INCLUDE[Compact](~/includes/compact-md.md)] Używa różne wersje tych obsługuje bibliotek, aby uniknąć użycia typy i funkcje językowe nie znajdujące się na urządzeniach.  
  
> [!NOTE]
>  `/sdkpath` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia. `/sdkpath` Opcja jest ustawiona, gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] urządzenia projektu jest ładowany.  
  
 Można określić, czy kompilator powinien skompilować bez odwołania do Visual Basic Runtime Library przy użyciu `/vbruntime` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki Mscorlib.dll i pliku Microsoft.VisualBasic.dll znajdujące się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C. Zazwyczaj należy użyć najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [/ vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a>/moduleassemblyname
Określa nazwę zestawu, którego częścią ma być ten moduł.  
  
## <a name="syntax"></a>Składnia  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`assembly_name`|Nazwa zestawu, którego częścią ma być ten moduł.|  
  
## <a name="remarks"></a>Uwagi  
 Procesy kompilatora `/moduleassemblyname` tylko wtedy, gdy opcja `/target:module` określono opcję. Powoduje to, że kompilator Utwórz moduł. Moduł, który został utworzony przez kompilator jest prawidłowa tylko dla zestawu określony za pomocą `/moduleassemblyname` opcji. Jeśli moduł zostanie umieszczony w innym zestawie, zostanie przeprowadzona błędów czasu wykonywania.  
  
 `/moduleassemblyname` Opcja jest potrzebna tylko wtedy, gdy spełnione są poniższe warunki:  
  
-   Typ danych w module musi mieć dostęp do `Friend` typu w zestawie.  
  
-   Przywoływany zestaw ma przyznane dostęp do przyjaznego zestawu do zestawu, do którego zostanie utworzony moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  `/moduleassemblyname` Opcja nie jest dostępne w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: kompilacja zestawów wieloplikowych](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/ addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [Zestawy i Globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)

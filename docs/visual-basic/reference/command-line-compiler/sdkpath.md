---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 2024ccadb06fdea0c24d9d304c2fe040f8cce1d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814331"
---
# <a name="-sdkpath"></a>-sdkpath
Określa lokalizację mscorlib.dll i Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Składnia  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Katalog zawierający wersji biblioteki mscorlib.dll i Microsoft.VisualBasic.dll na potrzeby kompilacji. Ta ścieżka nie została zweryfikowana, dopóki nie jest ładowany. Nazwę katalogu należy ująć w znaki cudzysłowu ("") zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja nakazuje kompilatorowi języka Visual Basic obciążenia mscorlib.dll i Microsoft.VisualBasic.dll pliki z lokalizacji innych niż domyślne. `-sdkpath` Opcja została zaprojektowana do użycia z [- netcf —](../../../visual-basic/reference/command-line-compiler/netcf.md). [!INCLUDE[Compact](~/includes/compact-md.md)] Używa różnych wersji tych Obsługa bibliotek, aby uniknąć użycia typów i funkcji języka, które nie znajdują się na urządzeniach.  
  
> [!NOTE]
>  `-sdkpath` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia. `-sdkpath` Ustawiono opcję po załadowaniu projektu urządzenia języka Visual Basic.  
  
 Można określić, czy kompilator powinien kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic przy użyciu `-vbruntime` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [- vbruntime —](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki Mscorlib.dll i Microsoft.VisualBasic.dll znajduje się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C. Zazwyczaj używasz najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

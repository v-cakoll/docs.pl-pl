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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004696"
---
# <a name="-sdkpath"></a>-sdkpath
Określa lokalizację plików mscorlib. dll i Microsoft. VisualBasic. dll.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Argumenty  
 `path`  
 Katalog zawierający wersje plików mscorlib. dll i Microsoft. VisualBasic. dll do użycia na potrzeby kompilacji. Ta ścieżka nie jest weryfikowana, dopóki nie zostanie załadowana. Nazwa katalogu powinna być ujęta w cudzysłów (""), jeśli zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja nakazuje kompilatorowi Visual Basic załadowanie plików mscorlib. dll i Microsoft. VisualBasic. dll z lokalizacji innej niż domyślna. Opcja `-sdkpath` została zaprojektowana tak, aby była używana z [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). .NET Compact Framework wykorzystuje różne wersje tych bibliotek, aby uniknąć używania typów i funkcji języka, które nie zostały odnalezione na urządzeniach.  
  
> [!NOTE]
> Opcja `-sdkpath` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia. Opcja `-sdkpath` jest ustawiana podczas ładowania projektu Visual Basic urządzenia.  
  
 Można określić, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic przy użyciu opcji kompilatora `-vbruntime`. Aby uzyskać więcej informacji, zobacz [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Myfile.vb` z .NET Compact Framework przy użyciu wersji plików mscorlib. dll i Microsoft. VisualBasic. dll znajdujących się w domyślnym katalogu instalacyjnym .NET Compact Framework na dysku C. Zazwyczaj należy użyć najnowszej wersji .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)

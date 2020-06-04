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
ms.openlocfilehash: 85aba17b330af1b25b39f462844bc1a4856a448a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403112"
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
 Ta opcja nakazuje kompilatorowi Visual Basic załadowanie plików mscorlib. dll i Microsoft. VisualBasic. dll z lokalizacji innej niż domyślna. `-sdkpath`Opcja została zaprojektowana tak, aby była używana z [-netcf](netcf.md). .NET Compact Framework wykorzystuje różne wersje tych bibliotek, aby uniknąć używania typów i funkcji języka, które nie zostały odnalezione na urządzeniach.  
  
> [!NOTE]
> `-sdkpath`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia. `-sdkpath`Opcja jest ustawiana podczas ładowania projektu urządzenia Visual Basic.  
  
 Można określić, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic przy użyciu `-vbruntime` opcji kompilatora. Aby uzyskać więcej informacji, zobacz [-vbruntime](vbruntime.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `Myfile.vb` się z .NET Compact Framework przy użyciu wersji plików mscorlib. dll i Microsoft. VisualBasic. dll znajdujących się w domyślnym katalogu instalacyjnym .NET Compact Framework na dysku C. Zazwyczaj należy użyć najnowszej wersji .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [-netcf](netcf.md)
- [-vbruntime](vbruntime.md)

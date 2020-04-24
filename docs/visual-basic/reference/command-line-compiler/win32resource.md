---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004962"
---
# <a name="-win32resource"></a>-win32resource
Wstawia plik zasobów Win32 do pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku zasobów, który ma zostać dodany do pliku wyjściowego. Nazwa pliku należy ująć w cudzysłów (""), jeśli zawiera spację.  
  
## <a name="remarks"></a>Uwagi  
 Plik zasobów Win32 można utworzyć za pomocą kompilatora zasobów systemu Microsoft Windows (RC).  
  
 Zasób Win32 może zawierać informacje o wersji lub mapie bitowej (ikony), które ułatwiają identyfikację aplikacji w **Eksploratorze plików**. Jeśli nie określisz `-win32resource`, kompilator generuje informacje o wersji na podstawie wersji zestawu. Opcje `-win32resource` i `-win32icon` wzajemnie się wykluczają.  
  
 Zobacz [-linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) , aby odwołać się do .NET Framework pliku zasobów, lub [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) , aby dołączyć plik zasobów .NET Framework.  
  
> [!NOTE]
> `-win32resource` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik zasobów Win32 `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

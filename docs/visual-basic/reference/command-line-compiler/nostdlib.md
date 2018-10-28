---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 957eca6066a316a4f4daf7e6de972df98082c26c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183299"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Powoduje, że kompilator nie automatycznie odwołuje się do standardowych bibliotek.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Uwagi  
 `-nostdlib` Opcja usuwa automatyczne odwołanie do zestawu System.dll i uniemożliwia odczytywanie soubor Vbc.rsp przez kompilator. Soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe, odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw.  
  
> [!NOTE]
>  Zestawy Mscorlib.dll i Microsoft.VisualBasic.dll zawsze są wywoływane.  
  
> [!NOTE]
>  `-nostdlib` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` bez odwołania do bibliotek standardowych. Należy ustawić `_MYTYPE` Stała kompilacji warunkowej do ciągu "Puste", aby usunąć `My` obiektu.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

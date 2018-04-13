---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Powoduje, że kompilator nie automatycznie odwołuje się do bibliotek standardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>Uwagi  
 `-nostdlib` Opcja usuwa automatyczne odwołanie do zestawu System.dll i zabezpiecza kompilator przed odczytem pliku Vbc.rsp. Pliku Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe, odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw.  
  
> [!NOTE]
>  Zawsze odwołuje się do pliku Mscorlib.dll i pliku Microsoft.VisualBasic.dll zestawów.  
  
> [!NOTE]
>  `-nostdlib` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` bez odwołania do bibliotek standardowych. Należy ustawić `_MYTYPE` kompilacja warunkowa stałej na ciąg "Empty", aby usunąć `My` obiektu.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

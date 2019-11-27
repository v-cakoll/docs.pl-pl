---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347913"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Powoduje, że kompilator nie będzie automatycznie odwoływać się do bibliotek standardowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-nostdlib` usuwa automatyczne odwołanie do zestawu System. dll i uniemożliwia kompilatorowi odczytywanie pliku VBC. rsp. Plik VBC. rsp, który znajduje się w tym samym katalogu co plik VBC. exe, odwołuje się do najczęściej używanych zestawów .NET Framework i importuje przestrzenie nazw `System` i `Microsoft.VisualBasic`.  
  
> [!NOTE]
> Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.  
  
> [!NOTE]
> Opcja `-nostdlib` nie jest dostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` bez odwoływania się do bibliotek standardowych. Aby usunąć obiekt `My`, należy ustawić wartość `_MYTYPE` stałej kompilacji warunkowej na ciąg "Empty".  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

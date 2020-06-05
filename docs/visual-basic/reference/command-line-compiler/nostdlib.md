---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 0934799853323110e73087ba6d8975c30f84d8f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387715"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Powoduje, że kompilator nie będzie automatycznie odwoływać się do bibliotek standardowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Uwagi  
 `-nostdlib`Opcja usuwa automatyczne odwołanie do zestawu System. dll i uniemożliwia kompilatorowi odczytywanie pliku VBC. rsp. Plik VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe, odwołuje się do najczęściej używanych zestawów .NET Framework i importuje `System` `Microsoft.VisualBasic` przestrzenie nazw.  
  
> [!NOTE]
> Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.  
  
> [!NOTE]
> `-nostdlib`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje się `T2.vb` bez odwoływania się do bibliotek standardowych. `_MYTYPE`Aby usunąć obiekt, należy ustawić stałą dla kompilacji warunkowej na ciąg "Empty" `My` .  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [-noconfig](noconfig.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Dostosowywanie, które obiekty są dostępne w My](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)

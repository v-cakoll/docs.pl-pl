---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344211"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Powoduje, że kompilator akceptuje tylko składnię, która jest uwzględniona w określonej Visual Basic wersji językowej.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Argumenty  
 `version`  
 Wymagana. Wersja języka do użycia podczas kompilacji. Akceptowane wartości to `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` i `latest`.

 Wszystkie liczby całkowite można także określić przy użyciu `.0` jako wersji pomocniczej, na przykład `11.0`.

 Możesz wyświetlić listę wszystkich możliwych wartości, określając `-langversion:?` w wierszu polecenia.  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-langversion` określa składnię akceptowaną przez kompilator. Na przykład jeśli określisz, że wersja językowa to 9,0, kompilator generuje błędy dla składni, która jest prawidłowa tylko w wersji 10,0 lub nowszej.  
  
 Tej opcji można użyć podczas tworzenia aplikacji przeznaczonych dla różnych wersji .NET Framework. Na przykład jeśli jesteś celem .NET Framework 3,5, możesz użyć tej opcji, aby upewnić się, że nie używasz składni z wersji językowej 10,0.  
  
 Można ustawić `-langversion` bezpośrednio tylko przy użyciu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Określanie konkretnej wersji .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `sample.vb` dla Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Określanie konkretnej wersji programu .NET Framework jako docelowej](/visualstudio/ide/visual-studio-multi-targeting-overview)

---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005261"
---
# <a name="-recurse"></a>-recurse
Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych określonego katalogu lub katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`  
 Element opcjonalny. Katalog, w którym ma zostać rozpoczęte wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Wymagany. Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 W nazwie pliku można użyć symboli wieloznacznych, aby skompilować wszystkie zgodne pliki w katalogu projektu bez użycia `-recurse`. Jeśli nazwa pliku wyjściowego nie zostanie określona, kompilator opiera się na nazwie pliku wyjściowego w pierwszym przetworzonym pliku wejściowym. Zwykle jest to pierwszy plik na liście plików skompilowanych podczas wyświetlania alfabetycznie. Z tego powodu najlepiej określić plik wyjściowy przy użyciu `-out` opcji.  
  
> [!NOTE]
> `-recurse` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje wszystkie pliki Visual Basic w bieżącym katalogu.  
  
```console
vbc *.vb  
```  
  
 Poniższe polecenie kompiluje wszystkie pliki Visual Basic w `Test\ABC` katalogu i wszystkie znajdujące się w nim katalogi, a następnie `Test.ABC.dll`generuje.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

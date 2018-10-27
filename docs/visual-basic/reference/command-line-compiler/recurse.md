---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 1edb648ec574c0052b7b8314f4ada710c8b0fe01
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183337"
---
# <a name="-recurse"></a>-recurse
Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych w określonym katalogu lub katalog projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`  
 Opcjonalna. Katalog, w którym chcesz rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Wymagana. Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 Można używać symboli wieloznacznych w nazwach plików do kompilacji wszystkie odpowiednie pliki w katalogu projektu bez użycia `-recurse`. Jeśli nazwa pliku wyjściowego nie jest określony, kompilator Określa nazwę pliku wyjściowego na pierwszego pliku wejściowego przetworzone. Zwykle jest to pierwszy plik listy plików skompilowany podczas wyświetlania w kolejności alfabetycznej. Z tego powodu najlepiej określić przy użyciu pliku wyjściowego jest `-out` opcji.  
  
> [!NOTE]
>  `-recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje wszystkie pliki języka Visual Basic w bieżącym katalogu.  
  
```console
vbc *.vb  
```  
  
 Poniższe polecenie kompiluje wszystkie pliki języka Visual Basic w `Test\ABC` katalog i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

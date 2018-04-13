---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-recurse"></a>-recurse
Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych katalogu określonego lub katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`  
 Opcjonalny. Katalog, w którym ma rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Wymagany. Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia `-recurse`. Jeśli nazwa pliku wyjściowego, nie zostanie określona, kompilator Określa nazwę pliku wyjściowego na pierwszy plik wejściowy przetworzone. Zwykle jest to pierwszy plik listy plików skompilowanych widzianego alfabetycznie. Z tego powodu najlepiej określić plik danych wyjściowych za pomocą `-out` opcji.  
  
> [!NOTE]
>  `-recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu.  
  
```console
vbc *.vb  
```  
  
 Poniższe polecenie kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików `Test\ABC` katalogu i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

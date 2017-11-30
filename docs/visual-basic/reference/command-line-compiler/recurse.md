---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a>/recurse
Kompiluje pliki kodu źródłowego we wszystkich katalogach podrzędnych katalogu określonego lub katalogu projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir`  
 Opcjonalny. Katalog, w którym ma rozpocząć wyszukiwanie. Jeśli nie zostanie określony, wyszukiwanie rozpoczyna się w katalogu projektu.  
  
 `file`  
 Wymagany. Pliki do wyszukania. Symbole wieloznaczne są dozwolone.  
  
## <a name="remarks"></a>Uwagi  
 Symbole wieloznaczne w nazwie pliku służy do Kompiluj wszystkie zgodne pliki w katalogu projektu bez użycia `/recurse`. Jeśli nazwa pliku wyjściowego, nie zostanie określona, kompilator Określa nazwę pliku wyjściowego na pierwszy plik wejściowy przetworzone. Zwykle jest to pierwszy plik listy plików skompilowanych widzianego alfabetycznie. Z tego powodu najlepiej określić plik danych wyjściowych za pomocą `/out` opcji.  
  
> [!NOTE]
>  `/recurse` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu.  
  
```  
vbc *.vb  
```  
  
 Poniższy kod kompiluje wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików `Test\ABC` katalogu i wszystkie jego katalogów, a następnie generuje `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

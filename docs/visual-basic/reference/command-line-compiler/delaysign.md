---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c979ada9984ef345ffbb6b5e29c2f30595c3074d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-delaysign"></a>-delaysign
Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.  
  
## <a name="syntax"></a>Składnia  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Użyj `-delaysign-` Jeśli chcesz całkowicie podpisane zestawu. Użyj `-delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawu i Rezerwacja miejsca na podpisem wyznaczania wartości skrótu. Wartość domyślna to `-delaysign-`.  
  
## <a name="remarks"></a>Uwagi  
 `-delaysign` Opcja nie ma znaczenia, chyba że używana z [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.  
  
 Na przykład za pomocą `-delaysign+`, deweloperów w organizacji można rozpowszechniać testu bez znaku testerów można zarejestrować przy użyciu pamięci podręcznej GAC i korzystać z zestawu. Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można pełni podpisać zestawu. Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, umożliwiając wszystkich deweloperów do pracy z zestawów.  
  
 Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić - delaysign w Visual Studio zintegrowane środowisko programistyczne  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **podpisywanie** kartę.  
  
3.  Ustaw wartość **opóźnienie tylko znak** pole.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

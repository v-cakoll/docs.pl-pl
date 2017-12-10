---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc457a1a32048441f82976488158f223e7e3e087
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="delaysign"></a>/delaysign
Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.  
  
## <a name="syntax"></a>Składnia  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Użyj `/delaysign-` Jeśli chcesz całkowicie podpisane zestawu. Użyj `/delaysign+` Jeśli chcesz umieścić klucz publiczny w zestawu i Rezerwacja miejsca na podpisem wyznaczania wartości skrótu. Wartość domyślna to `/delaysign-`.  
  
## <a name="remarks"></a>Uwagi  
 `/delaysign` Opcja nie ma znaczenia, chyba że używana z [/KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.  
  
 Na przykład za pomocą `/delaysign+`, deweloperów w organizacji można rozpowszechniać testu bez znaku testerów można zarejestrować przy użyciu pamięci podręcznej GAC i korzystać z zestawu. Po zakończeniu pracy w zestawie osoba odpowiedzialna za klucz prywatny organizacji można pełni podpisać zestawu. Ta segmentacji poszczególnych chroni klucz prywatny organizacji przed ujawnieniem, umożliwiając wszystkich deweloperów do pracy z zestawów.  
  
 Zobacz [tworzenie i zestawy Using Strong-Named](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić/DelaySign w programie Visual Studio zintegrowane środowisko deweloperskie  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Kliknij przycisk **podpisywanie** kartę.  
  
3.  Ustaw wartość **opóźnienie tylko znak** pole.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/ KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

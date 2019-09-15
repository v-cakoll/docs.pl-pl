---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 6d3c89d598714446e04ba40155951f771d474866
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971992"
---
# <a name="-delaysign"></a>-delaysign
Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.  
  
## <a name="syntax"></a>Składnia  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Użyj `-delaysign-` , jeśli chcesz użyć w pełni podpisanego zestawu. Użyj `-delaysign+` , jeśli chcesz umieścić klucz publiczny w zestawie i zarezerwować miejsce dla podpisanej wartości skrótu. Wartość domyślna to `-delaysign-`.  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-delaysign` nie ma żadnego efektu, chyba że zostanie użyta z [-KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md) lub [-containerer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym. Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest. Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.  
  
 Na przykład przy użyciu `-delaysign+`, deweloper w organizacji może rozpowszechniać niepodpisane wersje testów zestawu, które testerzy mogą zarejestrować w globalnej pamięci podręcznej zestawów i używać. Po zakończeniu pracy z zestawem osoba odpowiedzialna za klucz prywatny organizacji może w pełni podpisać zestaw. Ta compartmentalization chroni klucz prywatny organizacji przed ujawnieniem, jednocześnie pozwalając wszystkim deweloperom na współdziałanie z zestawami.  
  
 Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić-delaysign w zintegrowanym środowisku programistycznym programu Visual Studio  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.   
  
2. Kliknij kartę **podpisywanie** .  
  
3. Ustaw wartość w polu **Opóźnij tylko znak** .  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: b6a2f3ba0772d8f8c8c6a762a1be01703d21b778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403138"
---
# <a name="-rootnamespace"></a>-rootnamespace
Określa przestrzeń nazw dla wszystkich deklaracji typu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespace`|Nazwa przestrzeni nazw, w której należy ująć wszystkie deklaracje typu dla bieżącego projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz pliku wykonywalnego programu Visual Studio (devenv. exe) do kompilowania projektu utworzonego w zintegrowanym środowisku programistycznym programu Visual Studio, użyj, `-rootnamespace` Aby określić wartość <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości. Zobacz [przełączniki wiersza polecenia devenv](/visualstudio/ide/reference/devenv-command-line-switches) , aby uzyskać więcej informacji.  
  
 Użyj Dezasembler MSIL () środowiska uruchomieniowego języka wspólnego, `Ildasm.exe` Aby wyświetlić nazwy przestrzeni nazw w pliku wyjściowym.  
  
|Aby ustawić-RootNamespace w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **aplikacja** .<br />3. Zmodyfikuj wartość w polu **główna przestrzeń nazw** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i ujmuje wszystkie deklaracje typów w przestrzeni nazw `mynamespace` .  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Ildasm. exe (IL dezasembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)

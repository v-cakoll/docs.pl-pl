---
title: -highentropyva (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662858"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (C# Compiler Options)
**- Highentropyva** jądra Windows informuje o — opcja kompilatora czy określonego pliku wykonywalnego obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Ta opcja określa, że 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony za [— platforma: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) — opcja kompilatora obsługuje przestrzeni adresów wirtualnych o wysokiej entropii. Opcja jest domyślnie wyłączona. Użyj **- highentropyva +** lub **- highentropyva** ją włączyć.  
  
## <a name="remarks"></a>Uwagi  
 **- Highentropyva** opcja umożliwia zgodne wersje jądra Windows do użycia wyższy stopień entropii podczas losowego generowania układu przestrzeni adresów procesu jako część ASLR. Użycie wyższy stopień entropii oznacza, że większa liczba adresów może być przydzielona do regiony pamięci, takie jak stosy i stosów. W rezultacie jego trudniej jest intruzowi zgadnąć lokalizację konkretnego regionu pamięci.  
  
 Gdy **- highentropyva** — opcja kompilatora jest określony, obiektu docelowego pliku wykonywalnego i wszystkie moduły, od których zależy musi być w stanie obsłużyć wartości wskaźnika, które są większe niż 4 gigabajty (GB), uruchamianego jako procesu 64-bitowego.

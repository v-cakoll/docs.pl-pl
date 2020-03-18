---
title: -highentropyva (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606846"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (Opcje kompilatora C#)
Opcja kompilatora **-highentropyva** informuje jądro systemu Windows, czy dany plik wykonywalny obsługuje randomizację układu przestrzeni adresowej (ASLR) o wysokiej entropii.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Ta opcja określa, że 64-bitowy plik wykonywalny lub plik wykonywalny oznaczony opcją kompilatora [-platform:anycpu](./platform-compiler-option.md) obsługuje wirtualną przestrzeń adresową o wysokiej entropii. Opcja jest domyślnie wyłączona. Użyj **-highentropyva+** lub **-highentropyva,** aby go włączyć.  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-highentropyva** umożliwia zgodnym wersjom jądra systemu Windows użycie wyższych stopni entropii podczas losowania układu przestrzeni adresowej procesu jako części ASLR. Przy użyciu wyższych stopni entropii oznacza, że większa liczba adresów mogą być przydzielane do regionów pamięci, takich jak stosy i sterty. W rezultacie trudniej jest odgadnąć lokalizację określonego regionu pamięci.  
  
 Po określeniu opcji kompilatora **-highentropyva** docelowy plik wykonywalny i wszystkie moduły, od których zależy, muszą być w stanie obsługiwać wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy są uruchomione jako proces 64-bitowy.

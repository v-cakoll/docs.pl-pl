---
title: -highentropyva (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5746caed8c1bf61038c97a49987c4c168eef9f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="highentropyva-c-compiler-options"></a>/highentropyva (opcje kompilatora C#)
**/Highentropyva** — opcja kompilatora informuje jądra systemu Windows, czy określonego pliku wykonywalnego obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Ta opcja określa, że 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) — opcja kompilatora obsługuje wysokiej entropii wirtualnej przestrzeni adresowej. Opcja jest domyślnie wyłączona. Użyj **/highentropyva+** lub **/highentropyva** ją włączyć.  
  
## <a name="remarks"></a>Uwagi  
 **/Highentropyva** opcja umożliwia zgodne wersje jądra systemu Windows, aby użyć wyższy stopień entropii podczas losowego generowania układu przestrzeni adresów procesu jako część ASLR. Użycie wyższy stopień entropii oznacza, że większej liczby adresy mogą być przydzielone do regiony pamięci, takich jak stosy i stosów. W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.  
  
 Gdy **/highentropyva** określono opcję kompilatora, element docelowy pliku wykonywalnego i wszelkich modułów, których zależy musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy są na nich uruchomione jako proces 64-bitowy.

---
title: -checked (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173773"
---
# <a name="-checked-c-compiler-options"></a>-checked (Opcje kompilatora C#)
**Opcja -checked** określa, czy instrukcja arytmetyczna liczby całkowitej, która powoduje wartość, która znajduje się poza zakresem typu danych, a która nie znajduje się w zakresie [zaznaczonego](../keywords/checked.md) lub [niezaznaczonego](../keywords/unchecked.md) słowa kluczowego, powoduje wyjątek w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja arytmetyczna liczby całkowitej, która `checked` znajduje `unchecked` się w zakresie lub słowa kluczowego, nie podlega efektowi opcji **-checked.**  
  
 Jeśli instrukcja arytmetyczna liczby całkowitej, która `checked` nie `unchecked` znajduje się w zakresie lub słowa kluczowego powoduje wartość spoza zakresu typu danych i **-checked+** (lub **-checked)** jest używany w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania. Jeśli **-checked-** jest używany w kompilacji, że instrukcja nie powoduje wyjątek w czasie wykonywania.  
  
 Domyślną wartością dla tej opcji jest **-checked-**; kontrola przepełnienia jest wyłączona.

 Czasami zautomatyzowane narzędzia, które są używane do tworzenia dużych aplikacji set -checked do +. Jednym ze scenariuszy użycia -checked- jest zastąpienie globalnego domyślnego narzędzia, określając -checked-.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Kliknij przycisk **Zaawansowane.**  
  
4. Zmodyfikuj właściwość **Sprawdź przepełnienie arytmetyczne.**  
  
 Aby programowo uzyskać dostęp do <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>tej opcji kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `t2.cs`. Użycie `-checked` w poleceniu określa, że każda instrukcja arytmetyczna całkowita w `checked` pliku, która nie znajduje się w zakresie lub `unchecked` słowa kluczowego, a która powoduje wartość, która znajduje się poza zakresem typu danych, powoduje wyjątek w czasie wykonywania.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)

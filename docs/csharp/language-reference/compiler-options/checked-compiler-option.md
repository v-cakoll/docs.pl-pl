---
title: — zaznaczone (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606988"
---
# <a name="-checked-c-compiler-options"></a>— zaznaczone (C# opcje kompilatora)
Opcja **-** Check określa, czy instrukcja arytmetyczna liczb całkowitych, która skutkuje wartością, która jest poza zakresem danych, i która nie jest w zakresie [zaznaczonego](../keywords/checked.md) lub niesprawdzonego słowa [](../keywords/unchecked.md) kluczowego, powoduje wyjątek czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja arytmetyczna liczb całkowitych, która znajduje się w `checked` zakresie `unchecked` słowa kluczowego or, nie podlega wpływowi opcji **-Checked** .  
  
 Jeśli instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w `checked` zakresie `unchecked` słowa kluczowego lub, powoduje użycie wartości spoza zakresu typu danych i **-Checked +** (lub **-Checked**) jest używana w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania. Jeśli jest używana w kompilacji, ta instrukcja nie powoduje wyjątku w czasie wykonywania.  
  
 Wartość domyślna dla tej opcji to **-Checked-** ; Sprawdzanie przepełnienia jest wyłączone.
 
 Czasami zautomatyzowane narzędzia, które są używane do kompilowania zestawu dużych aplikacji, są sprawdzane w programie +. Jednym z scenariuszy użycia-checked-jest zastąpienie globalnego domyślnego narzędzia przez określenie-checked-.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu. Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Kliknij przycisk **Zaawansowane** .  
  
4. Zmodyfikuj **Sprawdzanie dla właściwości przeciążenia/** niedopełnienie.  
  
 Aby programowo uzyskać dostęp do tej opcji kompilatora <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>, zobacz.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `t2.cs`. Użycie `-checked` w poleceniu określa, że wszystkie liczby całkowite arytmetyczne w pliku, który nie znajduje się w zakresie `checked` słowa kluczowego `unchecked` or, i powoduje, że wartość jest poza zakresem typu danych, powoduje wyjątek w uruchomieniu pierwszym.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

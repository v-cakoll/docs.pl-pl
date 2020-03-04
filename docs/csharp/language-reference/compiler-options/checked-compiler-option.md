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
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239695"
---
# <a name="-checked-c-compiler-options"></a>— zaznaczone (C# opcje kompilatora)
Opcja **-** Check określa, czy instrukcja arytmetyczna liczb całkowitych, która skutkuje wartością, która jest poza zakresem danych, i która nie jest w zakresie [zaznaczonego](../keywords/checked.md) lub [niesprawdzonego](../keywords/unchecked.md) słowa kluczowego, powoduje wyjątek czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja arytmetyczna liczb całkowitych, która znajduje się w zakresie słowa kluczowego `checked` lub `unchecked`, nie podlega wpływowi opcji **-Checked** .  
  
 Jeśli instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w zakresie słowa kluczowego `checked` lub `unchecked`, daje w wyniku wartość spoza zakresu typu danych i **-Checked +** (lub **-Checked**) jest używana w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania. Jeśli **jest** używana w kompilacji, ta instrukcja nie powoduje wyjątku w czasie wykonywania.  
  
 Wartość domyślna dla tej opcji to **-Checked-**; Sprawdzanie przepełnienia jest wyłączone.
 
 Czasami zautomatyzowane narzędzia, które są używane do kompilowania zestawu dużych aplikacji, są sprawdzane w programie +. Jednym z scenariuszy użycia-checked-jest zastąpienie globalnego domyślnego narzędzia przez określenie-checked-.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu. Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Kliknij przycisk **Zaawansowane**.  
  
4. Zmodyfikuj właściwość **sprawdzania przepełnienia arytmetycznego** .  
  
 Aby programowo uzyskać dostęp do tej opcji kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje `t2.cs`. Użycie `-checked` w poleceniu określa, że jakakolwiek instrukcja arytmetyczna liczb całkowitych w pliku, który nie jest w zakresie `checked` lub `unchecked` słowa kluczowego, i spowoduje, że wartość jest spoza zakresu typu danych, powoduje wyjątek w czasie wykonywania.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

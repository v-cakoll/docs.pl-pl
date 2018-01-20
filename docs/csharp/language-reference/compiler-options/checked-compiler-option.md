---
title: -zaznaczone (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a>-zaznaczone (opcje kompilatora C#)
**-Zaznaczone** opcja określa, czy instrukcji arytmetyczne liczba całkowita, których wynikiem jest wartość, która jest poza zakresem typu danych, a nie jest w zakresie [zaznaczone](../../../csharp/language-reference/keywords/checked.md) lub [ Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe, powoduje, że wyjątek czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcję arytmetyczne liczba całkowita, która znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe nie podlega efekt **-zaznaczone** opcji.  
  
 Jeśli instrukcja arytmetyczne liczba całkowita, która nie znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe wynikiem jest wartość spoza zakresu typu danych i **-checked +** (**-zaznaczone**) jest używany w Kompilacja, że instrukcja powoduje wyjątek w czasie wykonywania. Jeśli **- zaznaczone -** jest używany w kompilacji, instrukcji nie powoduje wyjątek w czasie wykonywania.  
  
 Wartość domyślna dla tej opcji to **- zaznaczone -**. Jeden scenariusz użycia **- zaznaczone -** Trwa tworzenie dużych aplikacji. Niekiedy automatycznego narzędzia są używane do tworzenia takich aplikacji, a takie narzędzie może automatycznie ustawiony **-zaznaczone** do +. Domyślny globalny tego narzędzia można zastąpić, określając **- zaznaczone -**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony. Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** właściwości.  
  
 Aby uzyskać dostęp do tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `t2.cs`. Korzystanie z `-checked` w poleceniu Określa, że każda instrukcja arytmetyczne całkowitą w pliku nie jest w zakresie `checked` lub `unchecked` — słowo kluczowe i którego wynikiem jest wartość, która jest poza zakresem typu danych powoduje zgłoszenie wyjątku przy uruchomieniu czas.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  

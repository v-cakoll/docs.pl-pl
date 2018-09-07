---
title: -zaznaczone (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cf6fa0e87654d0f9d61f34ea9b29ad80921a5720
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084858"
---
# <a name="-checked-c-compiler-options"></a>-zaznaczone (opcje kompilatora C#)
**-Zaznaczone** opcja określa, czy instrukcję arytmetyczne liczba całkowita, która wynikiem jest wartość, która jest poza zakresem typu danych, a nie jest w zakresie [zaznaczone](../../../csharp/language-reference/keywords/checked.md) lub [ unchecked](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe, powoduje wyjątek czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcję arytmetyczne liczba całkowita, która znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe nie podlega efekt **-zaznaczone** opcji.  
  
 Jeśli instrukcję arytmetyczne liczba całkowita, która nie znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe wyniki w wartość spoza zakresu typu danych, i **-checked +** (lub **-zaznaczone**) jest używany w Kompilacja, że instrukcja powoduje wyjątek w czasie wykonywania. Jeśli **- zaznaczone -** jest używany w kompilacji, instrukcji nie powoduje wyjątek w czasie wykonywania.  
  
 Wartość domyślna tej opcji to **- zaznaczone -**; sprawdzanie przepełnienia jest wyłączona.
 
 Czasami zautomatyzowanych narzędzi, które są używane do budowania dużych aplikacji ustawione — sprawdzany w celu +. Jeden scenariusz użycia, - zaznaczone — jest zastąpienie domyślnie globalne dla tego narzędzia, określając - zaznaczone —.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony. Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** właściwości.  
  
 Aby uzyskać dostęp do tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `t2.cs`. Korzystanie z `-checked` w poleceniu Określa, że każda liczba całkowita instrukcja arytmetyczne w pliku, nie jest w zakresie `checked` lub `unchecked` — słowo kluczowe i którego wynikiem jest wartość, która znajduje się poza zakresem typu danych, powoduje wyjątek przy uruchomieniu czas.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  

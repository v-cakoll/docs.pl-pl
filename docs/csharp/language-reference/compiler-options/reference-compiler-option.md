---
title: — Odwołanie (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 4a96da3668a73368dd98055a9082479f162b7b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-reference-c-compiler-options"></a>— Odwołanie (opcje kompilatora C#)
**— Odwołanie** opcja powoduje, że kompilator, aby zaimportować [publicznego](../../../csharp/language-reference/keywords/public.md) wpisz informacje w określonym pliku w bieżącym projekcie, dzięki czemu można odwoływać się do metadanych z określonych plików zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku, który zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, obejmują osobne **— odwołanie** opcji dla każdego pliku.  
  
 `alias`  
 Prawidłowy C# identyfikator reprezentujące głównej przestrzeni nazw, który będzie zawierać wszystkie przestrzenie nazw w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Aby zaimportować z więcej niż jeden plik, obejmują **— odwołanie** opcji dla każdego pliku.  
  
 Pliki, które należy zaimportować musi zawierać manifestu; pliku wyjściowego musi zostały skompilowane z jednym z [-docelowy](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcje inne niż [-docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** jest krótka forma **— odwołanie**.  
  
 Użyj [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) Importowanie metadanych z pliku wyjściowego, który nie zawiera manifest zestawu.  
  
 Jeśli odwołanie zestawu (zestawów A), który odwołuje się do innego zestawu (zestaw B), konieczne będzie odwołanie do zestawu B jeśli:  
  
-   Typ używanej z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Wywołuje się pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z zestawu B.  
  
 Użyj [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) Aby określić katalog, w którym znajduje się co najmniej jednego odwołania do zestawów. **-Lib** temacie omówiono również katalogów, w których kompilator szuka zestawów.  
  
 Kompilator, aby rozpoznać typu w zestawie, a nie w module, konieczne można wymusić można rozpoznać typu, co można zrobić poprzez definiowanie wystąpienia typu. Istnieją inne sposoby rozwiązania nazwy typów w zestawie dla kompilatora: na przykład, jeśli można dziedziczyć po typie w zestawie, nazwa typu zostanie następnie rozpoznane przez kompilator.  
  
 Czasami zachodzi konieczność odwołania dwie różne wersje tego samego składnika od w jednym zestawie. Aby to zrobić, użyj alias suboption na **— odwołanie** przełącznika dla każdego pliku do rozróżniania między dwoma plikami. Ten alias będzie służyć jako kwalifikator nazwy składnika i zostanie rozwiązany do składnika w jeden z plików.  
  
 Csc pliku odpowiedzi (.rsp —), które odwołuje się do najczęściej używanych zestawów platformy .NET Framework, jest używany domyślnie. Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator, aby używał csc.rsp.  
  
> [!NOTE]
> W programie Visual Studio, użyj **Dodaj odwołanie** okno dialogowe. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Aby zapewnić zachowanie równoważne pomiędzy dodawaniem odwołań za pomocą `-reference` i różnice pomiędzy dodawaniem odwołań za pomocą **Dodaj odwołanie** okno dialogowe, zestaw **Osadź typy międzyoperacyjne** właściwości **False** dla zestawu, który dodajesz. **Wartość true,** jest wartością domyślną właściwości.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia [alias zewnętrzny](../../../csharp/language-reference/keywords/extern-alias.md) funkcji.  
  
 Kompilowanie pliku źródłowego i zaimportować metadane z `grid.dll` i `grid20.dll`, które zostały skompilowane wcześniej. Różne wersje tego samego składnika zawiera dwa pliki dll i korzystać z dwóch **— odwołanie** z opcjami alias do kompilowania pliku źródłowego. Opcje wyglądać następująco:  
  
 -reference:GridV1=grid.dll i - reference:GridV2=grid20.dll  
  
 Konfiguruje aliasów zewnętrznych "GridV1" i "GridV2", które zostaną użyte w programie za pomocą instrukcji zewnętrzny:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Po zakończeniu można odwołać się do formantu siatki z grid.dll dodając nazwy formantu z GridV1, jak to:  
  
```csharp  
GridV1::Grid  
```  
  
 Ponadto można odwołać się do formantu siatki z grid20.dll dodając nazwy formantu z GridV2 następująco:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

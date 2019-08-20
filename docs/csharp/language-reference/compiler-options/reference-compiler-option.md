---
title: -Reference (C# opcje kompilatora)
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
ms.openlocfilehash: 247fb222eaacdb5ee60df2dded3a857f0395eb34
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606571"
---
# <a name="-reference-c-compiler-options"></a>-Reference (C# opcje kompilatora)
Opcja **-Reference** powoduje, że kompilator importuje informacje o typie [publicznym](../keywords/public.md) w określonym pliku do bieżącego projektu, co pozwala na odwoływanie się do metadanych z określonych plików zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku, który zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, należy dołączyć osobną opcję **odwołania** dla każdego pliku.  
  
 `alias`  
 Prawidłowy C# identyfikator, który będzie reprezentować główną przestrzeń nazw, która będzie zawierać wszystkie przestrzenie nazw w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Aby zaimportować z więcej niż jednego pliku, należy dołączyć opcję **-odwołanie** dla każdego pliku.  
  
 Importowane pliki muszą zawierać manifest; plik wyjściowy musi być skompilowany za pomocą jednej z opcji [-Target](./target-compiler-option.md) [: module](./target-module-compiler-option.md).  
  
 **-r** jest krótką formą **odwołania**.  
  
 Użyj polecenia [-addmodule](./addmodule-compiler-option.md) , aby zaimportować metadane z pliku wyjściowego, który nie zawiera manifestu zestawu.  
  
 Jeśli odwołujesz się do zestawu (zestawu A), który odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:  
  
- Typ używany z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.  
  
- Wywołujesz pole, właściwość, zdarzenie lub metodę, która ma typ zwracany lub typ parametru z zestawu B.  
  
 Użyj [-lib](./lib-compiler-option.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu. W temacie **-lib** omówiono również katalogi, w których Kompilator wyszukuje zestawy.  
  
 Aby kompilator rozpoznawał typ w zestawie, a nie w module, należy go wymusić, aby rozpoznać typ, który można wykonać przez zdefiniowanie wystąpienia typu. Istnieją inne sposoby rozwiązywania nazw typów w zestawie dla kompilatora: na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu zostanie rozpoznana przez kompilator.  
  
 Czasami konieczne jest odwołanie się do dwóch różnych wersji tego samego składnika z jednego zestawu. Aby to zrobić, użyj opcji alias w przełączniku **odwołania** dla każdego pliku, aby rozróżnić oba pliki. Ten alias będzie używany jako kwalifikator dla nazwy składnika i zostanie rozpoznany jako składnik w jednym z tych plików.  
  
 Domyślnie używany jest plik odpowiedzi CSC (. RSP), który odwołuje się do najczęściej używanych zestawów .NET Framework. Użyj [-noconfig](./noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator korzystał z CSC. rsp.  
  
> [!NOTE]
> W programie Visual Studio Użyj okna dialogowego **Dodaj odwołanie** . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)odwołań. Aby zapewnić równoważne zachowanie między dodawaniem odwołań przy `-reference` użyciu i dodawaniu odwołań przy użyciu okna dialogowego **Dodaj odwołanie** , ustaw właściwość **Osadź typy** współdziałania na **wartość false** dla zestawu, który jest dodawany. Wartość **true** jest wartością domyślną właściwości.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak używać funkcji [alias zewnętrzny](../keywords/extern-alias.md) .  
  
 Kompilowanie pliku źródłowego i Importowanie metadanych z `grid.dll` i `grid20.dll`, które zostały wcześniej skompilowane. Dwie biblioteki DLL zawierają oddzielne wersje tego samego składnika, a do kompilowania pliku źródłowego służą dwa **odwołania** z opcjami aliasów. Opcje wyglądają następująco:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Powoduje to skonfigurowanie aliasów `GridV1` zewnętrznych i `GridV2`, które są używane w `extern` programie, za pomocą instrukcji:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Po wykonaniu tej czynności można odwołać się do formantu siatki z `grid.dll` , tworząc prefiks `GridV1`nazwy kontrolki, tak jak to:  
  
```csharp  
GridV1::Grid  
```  
  
 Ponadto można odwołać się do formantu siatki z `grid20.dll` , tworząc prefiks nazwy kontrolki w `GridV2` następujący sposób:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

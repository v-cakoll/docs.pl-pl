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
ms.openlocfilehash: 131cdf62917ab2fc8d564b85c30d13c8971e5809
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705024"
---
# <a name="-reference-c-compiler-options"></a>— Odwołanie (opcje kompilatora C#)
**— Dokumentacja** opcja powoduje, że kompilator, aby zaimportować [publicznych](../../../csharp/language-reference/keywords/public.md) wpisz informacje w określonym pliku do bieżącego projektu, dzięki czemu można odwoływać się do metadanych z określonych plików zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku, który zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, należy dołączyć oddzielnego **— dokumentacja** opcji dla każdego pliku.  
  
 `alias`  
 Prawidłowe identyfikatorem języka C#, która będzie reprezentować głównej przestrzeni nazw, który będzie zawierać wszystkie przestrzenie nazw w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Aby zaimportować z więcej niż jeden plik, należy dołączyć **— dokumentacja** opcji dla każdego pliku.  
  
 Pliki, które należy zaimportować musi zawierać manifest; Plik wyjściowy muszą być skompilowane przy użyciu jednego z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji innych niż [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** jest krótka forma **— dokumentacja**.  
  
 Użyj [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) Importowanie metadanych z pliku wyjściowego, który nie zawiera manifest zestawu.  
  
 Jeśli odwołujesz się zestaw (Assembly A), który odwołuje się do innego zestawu (Assembly B), konieczne będzie odwołanie do zestawu B jeśli:  
  
-   Typ używanej z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Wywołuje się, pola, właściwości, zdarzenia lub metody, która ma typ zwracany lub typu parametru z zestawu B.  
  
 Użyj [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów. **-Lib** temacie omówiono również katalogi, w których kompilator wyszukuje zestawy.  
  
 Kompilator rozpoznaje typu w zestawie, a nie w module, potrzebny zmuszeni do rozpoznania typu, co można zrobić, określając wystąpienie tego typu. Istnieją inne sposoby, aby rozwiązać nazwy typów w zestawie dla kompilatora: na przykład, jeśli możesz dziedziczyć z typu w zestawie, nazwa typu zostanie następnie być rozpoznawane przez kompilator.  
  
 Czasami zachodzi konieczność odwoływać się do dwóch różnych wersji jednego składnika, z poziomu jednego zestawu. Aby to zrobić, należy użyć alias suboption na **— dokumentacja** przełącznika dla każdego pliku w celu rozróżnienia między dwoma plikami. Ten alias będzie służyć jako kwalifikator nazwy składnika i zostanie rozwiązany do składnika w jeden z plików.  
  
 Csc pliku odpowiedzi (rsp), która odwołuje się do powszechnie stosowane zestawów .NET Framework, jest używany domyślnie. Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator korzystać csc.rsp.  
  
> [!NOTE]
> W programie Visual Studio, należy użyć **Dodaj odwołanie** okno dialogowe. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Aby zapewnić zachowanie równoważne między dodawaniem odwołań za pomocą `-reference` i dodawaniem odwołań za pomocą **Dodaj odwołanie** okno dialogowe, zestaw **Osadź typy współdziałania** właściwość **False** dla zestawu, który dodajesz. **Wartość true,** jest wartością domyślną dla właściwości.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak używać [alias zewnętrzny](../../../csharp/language-reference/keywords/extern-alias.md) funkcji.  
  
 Kompilowanie pliku źródłowego i zaimportować metadane z `grid.dll` i `grid20.dll`, które zostały skompilowane wcześniej. Dwa pliki dll zawiera różne wersje tego samego składnika, a następnie użyj dwóch **— dokumentacja** przy użyciu opcji alias do kompilowania pliku źródłowego. Opcje wyglądać następująco:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Powoduje to skonfigurowanie aliasów zewnętrznych `GridV1` i `GridV2`, używane w programie przez `extern` instrukcji:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Po zakończeniu tej operacji możesz zapoznać się z formant siatki z `grid.dll` przez dodanie przedrostka nazwę formantu `GridV1`, podobnie do następującego:  
  
```csharp  
GridV1::Grid  
```  
  
 Ponadto, możesz zapoznać się z formant siatki z `grid20.dll` przez dodanie przedrostka nazwę formantu `GridV2` następująco:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

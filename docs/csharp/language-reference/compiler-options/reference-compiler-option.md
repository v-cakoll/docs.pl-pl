---
title: -reference (Opcje kompilatora C#)
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
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173669"
---
# <a name="-reference-c-compiler-options"></a>-reference (Opcje kompilatora C#)
Opcja **-reference** powoduje, że kompilator importuje informacje o typie [publicznym](../keywords/public.md) w określonym pliku do bieżącego projektu, umożliwiając w ten sposób odwoływanie się do metadanych z określonych plików zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku, który zawiera manifest zestawu. Aby zaimportować więcej niż jeden plik, dołącz oddzielną opcję **-reference** dla każdego pliku.  
  
 `alias`  
 Prawidłowy identyfikator Języka C#, który będzie reprezentował główny obszar nazw, który będzie zawierał wszystkie obszary nazw w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Aby zaimportować z więcej niż jednego pliku, dołącz opcję **-reference** dla każdego pliku.  
  
 Importowane pliki muszą zawierać manifest; plik wyjściowy musi zostać skompilowany z jedną z opcji [-target](./target-compiler-option.md) innych niż [-target:module](./target-module-compiler-option.md).  
  
 **-r** jest krótką formą **-reference**.  
  
 Użyj [-addmodule](./addmodule-compiler-option.md) do importowania metadanych z pliku wyjściowego, który nie zawiera manifestu zestawu.  
  
 W przypadku odwoływania się do złożenia (zestawu A), który odwołuje się do innego złożenia (złożenia B), należy odwołać się do zestawu B, jeśli:  
  
- Typ używany z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
- Wywołanie pola, właściwości, zdarzenia lub metody, która ma typ zwracany lub typ parametru z zestawu B.  
  
 Użyj [-lib,](./lib-compiler-option.md) aby określić katalog, w którym znajduje się co najmniej jedno z odwołań do zestawu. Temat **-lib** omawia również katalogi, w których kompilator wyszukuje zestawy.  
  
 Aby kompilator rozpoznał typ w zestawie, a nie w module, musi być zmuszony do rozwiązania typu, co można zrobić, definiując wystąpienie typu. Istnieją inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora: na przykład, jeśli dziedziczysz po typie w zestawie, nazwa typu zostanie rozpoznana przez kompilator.  
  
 Czasami konieczne jest odwołanie się do dwóch różnych wersji tego samego komponentu z poziomu jednego złożenia. Aby to zrobić, należy użyć podopcji aliasu na przełączniku **-reference** dla każdego pliku, aby odróżnić dwa pliki. Ten alias będzie używany jako kwalifikator nazwy składnika i zostanie rozwiązany ze składnikiem w jednym z plików.  
  
 Plik odpowiedzi csc (.rsp), który odwołuje się do często używanych zestawów .NET Framework, jest używany domyślnie. Użyj [-noconfig,](./noconfig-compiler-option.md) jeśli nie chcesz, aby kompilator używał csc.rsp.  
  
> [!NOTE]
> W programie Visual Studio użyj okna dialogowego **Dodawanie odwołania.** Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Aby zapewnić równoważne zachowanie `-reference` między dodawaniem odwołań przy użyciu i dodawaniem odwołań przy użyciu okna dialogowego **Dodawanie odwołania,** ustaw właściwość **Embed Interop Types** na **False** dla zestawu, który dodajesz. **Wartość True** jest wartością domyślną właściwości.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak korzystać z funkcji [aliasu extern.](../keywords/extern-alias.md)  
  
 Skompilować plik źródłowy i `grid.dll` `grid20.dll`zaimportować metadane z i , które zostały skompilowane wcześniej. Dwa biblioteki DLL zawierają oddzielne wersje tego samego składnika i do skompilowania pliku źródłowego są używane **dwie** odwołania z opcjami aliasu. Opcje wyglądają tak:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Spowoduje to skonfigurowanie aliasów `GridV1` zewnętrznych i `GridV2`, których używasz `extern` w programie za pomocą instrukcji:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Gdy to zrobisz, można odwołać `grid.dll` się do kontroli siatki z preplikując nazwę formantu z `GridV1`, w ten sposób:  
  
```csharp  
GridV1::Grid  
```  
  
 Ponadto można odwoływać się do `grid20.dll` formantu siatki, `GridV2` poprzedzając nazwę formantu w ten sposób:  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -Resource (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602525"
---
# <a name="-resource-c-compiler-options"></a>-Resource (C# opcje kompilatora)
Osadza określony zasób w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów .NET Framework, który ma zostać osadzony w pliku wyjściowym.  
  
 `identifier`obowiązkowe  
 Nazwa logiczna zasobu; Nazwa, która jest używana do ładowania zasobu. Wartość domyślna to nazwa pliku.  
  
 `accessibility-modifier`obowiązkowe  
 Dostępność zasobu: Public lub Private. Wartość domyślna to Public.  
  
## <a name="remarks"></a>Uwagi  
 Użyj polecenia [-linkresource —](./linkresource-compiler-option.md) , aby połączyć zasób z zestawem, a nie dodać pliku zasobów do pliku wyjściowego.  
  
 Domyślnie zasoby są publiczne w zestawie, gdy są tworzone przy użyciu C# kompilatora. Aby udostępnić zasoby jako prywatne, określ `private` jako modyfikator dostępności. Żadna inna dostępność jest inna `public` niż `private` lub niedozwolona.  
  
 Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać <xref:System.Resources> za pomocą elementów członkowskich w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. W przypadku wszystkich innych zasobów Użyj `GetManifestResource` metod <xref:System.Reflection.Assembly> w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 **-res** to krótka forma **zasobu**.  
  
 Kolejność zasobów w pliku wyjściowym jest określana na podstawie kolejności określonej w wierszu polecenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Dodaj plik zasobów do projektu.  
  
2. Wybierz plik, który ma zostać osadzony w **Eksplorator rozwiązań**.  
  
3. Wybierz pozycję **Akcja kompilacji** dla pliku w oknie **Właściwości** .  
  
4. Ustaw **akcję kompilacji** na **zasób osadzony**.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.FileProperties2.BuildAction%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Dołącz plik `rf.resource`zasobu:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

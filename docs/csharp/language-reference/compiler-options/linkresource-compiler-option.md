---
title: -linkresource — (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606752"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource — (C# opcje kompilatora)
Tworzy łącze do zasobu .NET Framework w pliku wyjściowym. Plik zasobów nie został dodany do pliku wyjściowego. Różni się to od opcji [-Resource](./resource-compiler-option.md) , która osadza plik zasobów w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów .NET Framework, do którego chcesz utworzyć łącze z zestawu.  
  
 `identifier`obowiązkowe  
 Nazwa logiczna zasobu; Nazwa, która jest używana do ładowania zasobu. Wartość domyślna to nazwa pliku.  
  
 `accessibility-modifier`obowiązkowe  
 Dostępność zasobu: Public lub Private. Wartość domyślna to Public.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie połączone zasoby są publiczne w zestawie, gdy są tworzone przy użyciu C# kompilatora. Aby udostępnić zasoby jako prywatne, określ `private` jako modyfikator dostępności. Inny modyfikator inny niż `public` lub `private` jest niedozwolony.  
  
 **-linkresource —** wymaga jednej z opcji [-Target](./target-compiler-option.md) innych niż **-target: module**.  
  
 Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać <xref:System.Resources> za pomocą elementów członkowskich w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. W przypadku wszystkich innych zasobów Użyj `GetManifestResource` metod <xref:System.Reflection.Assembly> w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Plik określony w `filename` może być dowolnym formatem. Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie. W drugim z poniższych przykładów pokazano, jak to zrobić. Tę samą czynność można wykonać w konsolidatorze zestawu. Trzeci z poniższych przykładów pokazuje, jak to zrobić. Aby uzyskać więcej informacji, zobacz [Al. exe (Konsolidator zestawu)](../../../framework/tools/al-exe-assembly-linker.md) i [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** jest krótką formą **-linkresource —** .  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Połącz z plikiem `rf.resource`zasobów:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Przykład  
 Kompiluj `A.cs` do biblioteki DLL, połącz ją z natywną biblioteką DLL N. dll i umieść dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC). W tym przykładzie zarówno plik. dll, jak i N. dll będą znajdować się w pamięci podręcznej GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład wykonuje te same czynności co w poprzednim, ale przy użyciu opcji konsolidatora zestawu.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Al.exe (konsolidator zestawów)](../../../framework/tools/al-exe-assembly-linker.md)
- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)

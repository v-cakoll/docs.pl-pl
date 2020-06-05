---
title: Typ „<typename>” nie jest zdefiniowany
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386935"
---
# <a name="type-typename-is-not-defined"></a>Typ „\<typename>” nie jest zdefiniowany
Instrukcja utworzyła odwołanie do typu, który nie został zdefiniowany. Można zdefiniować typ w instrukcji deklaracji, takiej jak,, `Enum` `Structure` `Class` , lub `Interface` .  
  
 **Identyfikator błędu:** BC30002  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że definicja typu i jego odwołanie używają tej samej pisowni.  
  
- Upewnij się, że definicja typu jest dostępna dla odwołania. Na przykład, jeśli typ znajduje się w innym module i został zadeklarowany `Private` , Przenieś definicję typu do modułu odwołującego lub Zadeklaruj go `Public` .  
  
- Upewnij się, że przestrzeń nazw typu nie jest ponownie zdefiniowana w ramach projektu. Jeśli jest, użyj `Global` słowa kluczowego, aby w pełni zakwalifikować nazwę typu. Na przykład jeśli projekt definiuje przestrzeń nazw o nazwie `System` , nie można <xref:System.Object?displayProperty=nameWithType> uzyskać dostępu do typu, chyba że jest on w pełni kwalifikowany za pomocą `Global` słowa kluczowego: `Global.System.Object` .  
  
- Jeśli typ jest zdefiniowany, ale Biblioteka obiektów lub biblioteka typów, w której jest zdefiniowana, nie jest zarejestrowana w Visual Basic, kliknij przycisk **Dodaj odwołanie** w menu **projekt** , a następnie wybierz odpowiednią bibliotekę obiektów lub bibliotekę typów.  
  
- Upewnij się, że typ znajduje się w zestawie, który jest częścią profilowania .NET Framework profilu. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów .NET Framework określania błędów](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Zobacz też

- [Przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Enum, instrukcja](../statements/enum-statement.md)
- [Structure — Instrukcja](../statements/structure-statement.md)
- [Class, instrukcja](../statements/class-statement.md)
- [Interface, instrukcja](../statements/interface-statement.md)
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)

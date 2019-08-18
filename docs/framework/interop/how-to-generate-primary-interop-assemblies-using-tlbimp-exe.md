---
title: 'Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67b9b48587802b43e90a7f35ab8cbb3b2ee025b0
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567261"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe

Istnieją dwa sposoby generowania podstawowego zestawu międzyoperacyjnego:

- Przy użyciu [importera biblioteki typów (Tlbimp. exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) dostarczonego przez Windows SDK.

  Najbardziej prostym sposobem tworzenia podstawowych zestawów międzyoperacyjnych jest użycie [Tlbimp. exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp. exe zapewnia następujące zabezpieczenia:

  - Sprawdza inne zarejestrowane podstawowe zestawy międzyoperacyjności przed utworzeniem nowych zestawów międzyoperacyjnych dla dowolnych odwołań do bibliotek typów zagnieżdżonych.

  - Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontenera lub nazwy pliku w celu uzyskania silnej nazwy podstawowego zestawu międzyoperacyjnego.

  - Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku pominięcia odwołań do zestawów zależnych.

  - Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku dodania odwołań do zestawów zależnych, które nie są zestawami podstawowych międzyoperacyjnych.

- Ręczne tworzenie podstawowych zestawów międzyoperacyjnych w kodzie źródłowym przy użyciu języka zgodnego z Common Language Specification (CLS), takiego jak C#. Takie podejście jest przydatne, gdy biblioteka typów jest niedostępna.

Aby podpisać zestaw za pomocą silnej nazwy, musisz mieć parę kluczy kryptograficznych. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie pary kluczy](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Aby wygenerować podstawowy zestaw międzyoperacyjny przy użyciu programu Tlbimp. exe

1. W wierszu polecenia wpisz polecenie:

    **Tlbimp** *tlbfile* **/Primary/keyfile:** *Nazwa pliku* **/out:** *AssemblyName*

    W tym poleceniu *tlbfile* jest plikiem zawierającym bibliotekę typów com, *filename* jest nazwą kontenera lub pliku, który zawiera parę kluczy, a *AssemblyName* jest nazwą zestawu do podpisania silną nazwą.

Podstawowe zestawy międzyoperacyjności mogą odwoływać się tylko do innych podstawowych zestawów międzyoperacyjnych. Jeśli zestaw odwołuje się do typów z biblioteki typu COM innej firmy, należy uzyskać podstawowy zestaw międzyoperacyjny od wydawcy, aby można było wygenerować podstawowy zestaw międzyoperacyjny. Jeśli jesteś wydawcą, musisz wygenerować podstawowy zestaw międzyoperacyjny dla zależnej biblioteki typów przed wygenerowaniem podstawowego zestawu międzyoperacyjności.

Zależny podstawowy zestaw międzyoperacyjny z numerem wersji, który różni się od oryginalnej biblioteki typów, nie jest wykrywalny w przypadku instalacji w bieżącym katalogu. Należy zarejestrować zależny podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyć opcji **/Reference** , aby upewnić się, że Tlbimp. exe odnajdzie ZALEŻNĄ bibliotekę DLL.

Możesz również otoczyć wiele wersji biblioteki typów. Aby uzyskać instrukcje, [zobacz How to: Zawiń wiele wersji bibliotek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100))typów.

## <a name="example"></a>Przykład

Poniższy przykład importuje bibliotekę `LibUtil.tlb` typów com i podpisuje zestaw `LibUtil.dll` za pomocą silnej nazwy przy użyciu pliku `CompanyA.snk`klucza. Pomijając konkretną nazwę przestrzeni nazw, ten przykład tworzy domyślną przestrzeń nazw, `LibUtil`.

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Aby uzyskać bardziej opisową nazwę (przy użyciu *NazwaDostawcy*. *LibraryName* nazewnictwo, w poniższym przykładzie zastępuje domyślną nazwę pliku zestawu i nazwę przestrzeni nazw.

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

Poniższy przykład importuje `MyLib.tlb`, który odwołuje `CompanyA.LibUtil.dll`się i podpisuje `CompanyB.MyLib.dll` zestaw silną nazwą przy użyciu pliku `CompanyB.snk`klucza. Przestrzeń nazw, `CompanyB.MyLib`zastępuje domyślną nazwę przestrzeni nazw.

```
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)

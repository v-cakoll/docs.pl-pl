---
title: 'Instrukcje: Tworzenie zasad wydawcy'
description: Dowiedz się, jak dostawcy zestawu mogą utworzyć plik zasad wydawcy z uaktualnionym zestawem w programie .NET, aby określić, że aplikacje mają korzystać z nowszej wersji.
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105398"
---
# <a name="how-to-create-a-publisher-policy"></a>Instrukcje: Tworzenie zasad wydawcy

Dostawcy zestawów mogą określać, że aplikacje powinny korzystać z nowszej wersji zestawu, dołączając plik zasad wydawcy z uaktualnionym zestawem. Plik zasad wydawcy określa przekierowania zestawu i ustawienia podstawowe kodu, a także używa tego samego formatu co plik konfiguracyjny aplikacji. Plik zasad wydawcy jest kompilowany do zestawu i umieszczany w globalnej pamięci podręcznej zestawów.

Tworzenie zasad wydawcy obejmuje trzy kroki:

1. Utwórz plik zasad wydawcy.

2. Utwórz zestaw zasad wydawcy.

3. Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.

Schemat zasad wydawcy został opisany w temacie [przekierowywanie wersji zestawu](redirect-assembly-versions.md). Poniższy przykład pokazuje plik zasad wydawcy, który przekierowuje jedną wersję programu `myAssembly` do innej.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Aby dowiedzieć się, jak określić bazę kodu, zobacz [Określanie lokalizacji zestawu](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Tworzenie zestawu zasad wydawcy

Użyj [konsolidatora zestawu (Al.exe)](../tools/al-exe-assembly-linker.md) , aby utworzyć zestaw zasad wydawcy.

#### <a name="to-create-a-publisher-policy-assembly"></a>Aby utworzyć zestaw zasad wydawcy

W wierszu polecenia wpisz następujące polecenie:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

W tym poleceniu:

- `publisherPolicyFile`Argument jest nazwą pliku zasad wydawcy.

- `publisherPolicyAssemblyFile`Argument jest nazwą zestawu zasad wydawcy, który jest wynikiem tego polecenia. Nazwa pliku zestawu musi być zgodna z formatem:

  "policy.majorNumber.minorNumber.mainAssemblyName.dll"

- `keyPairFile`Argument jest nazwą pliku zawierającego parę kluczy. Należy podpisać zestaw i zestaw zasad wydawcy z tą samą parą kluczy.

- `processorArchitecture`Argument identyfikuje platformę objętą przez zestaw specyficzny dla procesora.

  > [!NOTE]
  > Możliwość określania architektury procesora zależy od .NET Framework 2,0.

Możliwość określania architektury procesora zależy od .NET Framework 2,0. Następujące polecenie tworzy zestaw zasad wydawcy wywoływany `policy.1.0.myAssembly` z pliku zasad wydawcy o nazwie `pub.config` , przypisuje silną nazwę do zestawu przy użyciu pary kluczy w `sgKey.snk` pliku i określa, że zestaw jest przeznaczony dla architektury procesora x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Zestaw zasad wydawcy musi być zgodny z architekturą procesora zestawu, którego dotyczy. W takim przypadku, jeśli zestaw ma <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> wartość <xref:System.Reflection.ProcessorArchitecture.MSIL> , zestaw zasad wydawcy dla tego zestawu musi być utworzony przy użyciu `/platform:anycpu` . Należy podać osobny zestaw zasad wydawcy dla każdego zestawu specyficznego dla procesora.

Wynikiem tej reguły jest zmiana architektury procesora dla zestawu, dlatego należy zmienić składnik główny lub pomocniczy numeru wersji, aby można było dostarczyć nowy zestaw zasad wydawcy z poprawną architekturą procesora. Stary zestaw zasad wydawcy nie może obtworzyć zestawu, gdy zestaw ma inną architekturę procesora.

Inna konsekwencja polega na tym, że konsolidator w wersji 2,0 nie może zostać użyty do utworzenia zestawu zasad wydawcy dla zestawu skompilowanego przy użyciu wcześniejszych wersji .NET Framework, ponieważ zawsze określa architekturę procesora.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Dodawanie zestawu zasad wydawcy do globalnej pamięci podręcznej zestawów

Użyj [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) , aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów

W wierszu polecenia wpisz następujące polecenie:

```console
gacutil /i publisherPolicyAssemblyFile
```

Następujące polecenie dodaje `policy.1.0.myAssembly.dll` do globalnej pamięci podręcznej zestawów.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Zestawu zasad wydawcy nie można dodać do globalnej pamięci podręcznej zestawów, chyba że oryginalny plik zasad wydawcy określony w argumencie znajduje się `/link` w tym samym katalogu, w którym znajduje się zestaw.

## <a name="see-also"></a>Zobacz też

- [Programowanie za pomocą zestawów](../../standard/assembly/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji za pomocą plików konfiguracji](index.md)
- [Schemat ustawień środowiska uruchomieniowego](./file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](./file-schema/index.md)
- [Przekierowywanie wersji zestawu](redirect-assembly-versions.md)

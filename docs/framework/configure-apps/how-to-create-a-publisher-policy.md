---
title: 'Porady: tworzenie zasad wydawcy'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646059"
---
# <a name="how-to-create-a-publisher-policy"></a>Porady: tworzenie zasad wydawcy

Dostawcy zestawów można stwierdzić, że aplikacje powinny używać nowszej wersji zestawu, dołączając plik zasad wydawcy z uaktualnionego zestawu. Plik zasad wydawcy określa przekierowanie zestawu i ustawienia podstawowe kodu i używa tego samego formatu co plik konfiguracji aplikacji. Plik zasad wydawcy jest kompilowany do zestawu i umieszczany w globalnej pamięci podręcznej zestawów.

Tworzenie zasad wydawcy jest trzy kroki:

1. Tworzenie pliku zasad wydawcy.

2. Tworzenie zestawu zasad wydawcy.

3. Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.

Schemat zasad wydawcy jest opisany w [przekierowywaniu wersji zestawu](redirect-assembly-versions.md). W poniższym przykładzie przedstawiono plik zasad `myAssembly` wydawcy, który przekierowuje jedną wersję do innej.

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

Aby dowiedzieć się, jak określić podstawę kodu, zobacz [Określanie lokalizacji zestawu](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Tworzenie zestawu zasad wydawcy

Użyj [zestawu łączącego zestawu (Al.exe),](../tools/al-exe-assembly-linker.md) aby utworzyć zestaw zasad wydawcy.

#### <a name="to-create-a-publisher-policy-assembly"></a>Aby utworzyć zestaw zasad wydawcy

W wierszu polecenia wpisz następujące polecenie:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

W tym poleceniu:

- Argument `publisherPolicyFile` jest nazwą pliku zasad wydawcy.

- Argument `publisherPolicyAssemblyFile` jest nazwą zestawu zasad wydawcy, który wynika z tego polecenia. Nazwa pliku złożenia musi być zgodna z formatem:

  'policy.majorNumber.minorNumber.mainAssemblyName.dll'

- Argument `keyPairFile` jest nazwą pliku zawierającego parę kluczy. Należy podpisać zestaw zasad zestawu i wydawcy z tą samą parą kluczy.

- Argument `processorArchitecture` identyfikuje platformę, na podstawie których ma odpowiadać zestaw specyficzny dla procesora.

  > [!NOTE]
  > Możliwość kierowania na architekturę określonego procesora jest dostępna począwszy od programu .NET Framework 2.0.

Możliwość kierowania na architekturę określonego procesora jest dostępna począwszy od programu .NET Framework 2.0. Następujące polecenie tworzy zestaw zasad `policy.1.0.myAssembly` wydawcy wywoływany `pub.config`z pliku zasad wydawcy o nazwie , `sgKey.snk` przypisuje silną nazwę do zestawu przy użyciu pary kluczy w pliku i określa, że zestaw jest przeznaczony dla architektury procesora x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

Zestaw zasad wydawcy musi być zgodny z architekturą procesora zestawu, który ma zastosowanie do. W związku z tym <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> jeśli <xref:System.Reflection.ProcessorArchitecture.MSIL>zestaw ma wartość , zestaw zasad `/platform:anycpu`wydawcy dla tego zestawu musi być utworzony za pomocą . Należy podać oddzielny zestaw zasad wydawcy dla każdego zestawu specyficznego dla procesora.

Konsekwencją tej reguły jest to, że aby zmienić architekturę procesora dla zestawu, należy zmienić główny lub pomocniczy składnik numeru wersji, aby można było dostarczyć nowy zestaw zasad wydawcy z właściwą architekturą procesora. Stary zestaw zasad wydawcy nie może obsługiwać zestawu, gdy zestaw ma inną architekturę procesora.

Inną konsekwencją jest to, że konsolidator wersji 2.0 nie może służyć do tworzenia zestawu zasad wydawcy dla zestawu skompilowanego przy użyciu wcześniejszych wersji programu .NET Framework, ponieważ zawsze określa architekturę procesora.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Dodawanie zestawu zasad wydawcy do globalnej pamięci podręcznej zestawów

Użyj [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe),](../tools/gacutil-exe-gac-tool.md) aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów

W wierszu polecenia wpisz następujące polecenie:

```console
gacutil /i publisherPolicyAssemblyFile
```

Następujące polecenie `policy.1.0.myAssembly.dll` dodaje do globalnej pamięci podręcznej zestawów.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> Zestawu zasad wydawcy nie można dodać do globalnej pamięci podręcznej zestawów, chyba że oryginalny plik zasad wydawcy określony w `/link` argumie znajduje się w tym samym katalogu co zestaw.

## <a name="see-also"></a>Zobacz też

- [Programowanie za pomocą zestawów](../../standard/assembly/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji za pomocą plików konfiguracji](index.md)
- [Schemat ustawień środowiska uruchomieniowego](./file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](./file-schema/index.md)
- [Przekierowywanie wersji zestawu](redirect-assembly-versions.md)

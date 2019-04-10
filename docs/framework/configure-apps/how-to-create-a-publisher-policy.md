---
title: 'Instrukcje: Tworzenie zasad wydawcy'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: ed73b9c15d5d9279b97063077f210d3ac5dc68e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227395"
---
# <a name="how-to-create-a-publisher-policy"></a>Instrukcje: Tworzenie zasad wydawcy
Dostawcy zestawów mogą stanu, aplikacje powinny używać nowszej wersji zestawu, dołączając plik zasad wydawcy w z uaktualnionych zestawu. Plik zasad wydawcy określa przekierowanie zestawu i podstawowe ustawienia kodu i ma taki sam format jak plik konfiguracji aplikacji. Plik zasad wydawcy jest skompilowany w zestawie i umieszczone w globalnej pamięci podręcznej.  
  
 Istnieją trzy kroki związane z tworzeniem zasad wydawcy:  
  
1.  Utwórz plik zasad wydawcy.  
  
2.  Utwórz zestaw zasad wydawcy.  
  
3.  Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej.  
  
 Schemat dla zasad wydawcy jest opisana w [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md). W poniższym przykładzie pokazano wydawcy pliku zasad, który przekierowuje jedną wersję `myAssembly` do innego.  
  
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
  
 Aby dowiedzieć się, jak określić bazy kodu, zobacz [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Tworzenie zestaw zasad wydawcy  
 Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) można utworzyć zestawu zasad wydawcy.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Aby utworzyć zestaw zasad wydawcy  
  
1.  Wpisz następujące polecenie w wierszu polecenia:  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     W tym poleceniu:  
  
    -   *PublisherPolicyFile* argument jest nazwą plik zasad wydawcy.  
  
    -   *PublisherPolicyAssemblyFile* argument jest nazwą zestaw zasad wydawcy, która wynika z tego polecenia. Nazwy pliku zestawu musi być zgodny z formatem:  
  
         **zasady.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* argument jest nazwą pliku zawierającego parę kluczy. Musisz zarejestrować zestaw i zestaw zasad wydawcy z tej samej pary kluczy.  
  
    -   *ProcessorArchitecture* argument określa platformy docelowej zestawu specyficznych dla procesora.  
  
        > [!NOTE]
        >  Pozwalają objąć architektury określonemu procesorowi jest nowa w .NET Framework w wersji 2.0.  
  
     Następujące polecenie tworzy zestaw zasad wydawcy, o nazwie `policy.1.0.myAssembly` z plik zasad wydawcy o nazwie `pub.config`, przypisuje silnej nazwy zestawu, używając pary kluczy w `sgKey.snk` pliku i określa, że zestaw jest przeznaczony dla x86 Architektura procesora.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Zestaw zasad wydawcy muszą być zgodne zestawu, który ma zastosowanie do architektury procesora. W związku z tym jeśli zestaw ma <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> wartość <xref:System.Reflection.ProcessorArchitecture.MSIL>, zestaw zasad wydawcy dla tego zestawu musi zostać utworzona z `/platform:anycpu`. Należy podać oddzielny zestaw zasad wydawcy dla każdego zestawu specyficznych dla procesora.  
  
     Konsekwencji tej zasady jest, aby zmienić architektury procesora dla zestawu, należy zmienić mniejszym lub większym stopniu część numeru wersji, dzięki czemu można dostarczyć nowy zestaw zasad wydawcy przy użyciu poprawnej architektury procesora. Stary zestaw zasad wydawcy nie może obsłużyć zestawu, gdy zestaw ma architekturę inny procesor.  
  
     Inny konsekwencją jest, że konsolidator w wersji 2.0 nie można utworzyć zestaw zasad wydawcy, do zestawu skompilowanego we wcześniejszych wersjach programu .NET Framework, ponieważ określa on zawsze architektury procesora.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Dodawanie zestaw zasad wydawcy do globalnej pamięci podręcznej  
 Użyj [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej  
  
1.  Wpisz następujące polecenie w wierszu polecenia:  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     Następujące polecenie dodaje `policy.1.0.myAssembly.dll` do globalnej pamięci podręcznej.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Nie można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej, chyba że oryginalny plik zasad wydawcy znajduje się w tym samym katalogu co zestaw.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji za pomocą plików konfiguracji](../../../docs/framework/configure-apps/index.md)
- [Schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)
- [Przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md)

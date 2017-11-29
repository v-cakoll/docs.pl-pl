---
title: 'Porady: tworzenie zasad wydawcy'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 430426e3662582bd904bc088a362e9d7ed331c11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-publisher-policy"></a>Porady: tworzenie zasad wydawcy
Dostawców zestawy mogą stanu aplikacje powinny używać nowszej wersji zestawu przez dołączenie pliku zasad wydawcy w zestawie uaktualniony. Plik zasad wydawcy określa przekierowanie zestawów i kod podstawowych ustawień i używa tego samego formatu co plik konfiguracji aplikacji. Plik zasad wydawcy są kompilowane do zestawu i umieszczane w pamięci podręcznej GAC.  
  
 Istnieją trzy kroki związane z tworzeniem zasad wydawcy:  
  
1.  Utwórz plik zasad wydawcy.  
  
2.  Utwórz zestaw zasad wydawcy.  
  
3.  Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.  
  
 Schemat dla zasad wydawcy jest opisany w [przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md). W poniższym przykładzie przedstawiono wydawcy pliku zasad, który przekierowuje jednej wersji `myAssembly` na inny.  
  
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
  
 Aby dowiedzieć się, jak określać ścieżki bazowej kodu, zobacz [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Tworzenie zestaw zasad wydawcy  
 Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) można utworzyć zestaw zasad wydawcy.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Aby utworzyć zestaw zasad wydawcy  
  
1.  Wpisz następujące polecenie w wierszu polecenia:  
  
     **Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/KeyFile:**  *keyPairFile* **/platform:** *processorArchitecture*  
  
     W tym poleceniu:  
  
    -   *PublisherPolicyFile* argument jest nazwą pliku zasad wydawcy.  
  
    -   *PublisherPolicyAssemblyFile* argument jest nazwą zestaw zasad wydawcy, która wynika z tego polecenia. Nazwa pliku zestawu musi mieć format:  
  
         **zasady.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile* argument jest nazwą pliku zawierającego pary kluczy. Musisz zalogować się zestaw i zestaw zasad wydawcy z tej samej pary kluczy.  
  
    -   *ProcessorArchitecture* argument identyfikuje platformy docelowej zestawu specyficznych dla procesora.  
  
        > [!NOTE]
        >  Możliwość architekturę procesora w określonym celem jest nowa w programie .NET Framework w wersji 2.0.  
  
     Poniższe polecenie tworzy zestaw zasad wydawcy o nazwie `policy.1.0.myAssembly` z pliku zasad wydawcy o nazwie `pub.config`, przypisuje silnej nazwy zestawu przy użyciu pary kluczy w `sgKey.snk` pliku i określa, że zestaw jest przeznaczony dla x86 architektury procesora.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     Zestaw zasad wydawcy musi odpowiadać architekturze procesora stosowanym do zestawu. W związku z tym jeśli ma używanemu zestawowi <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> wartość <xref:System.Reflection.ProcessorArchitecture.MSIL>, zestaw zasad wydawcy dla tego zestawu musi zostać utworzona z `/platform:anycpu`. Należy podać osobny zestaw zasad wydawcy dla każdego zestawu specyficznych dla procesora.  
  
     Konsekwencji tej zasady jest, że aby można było zmienić architektury procesora dla zestawu, należy zmienić mniejszym lub składnik numeru wersji tak, aby można dostarczyć nowy zestaw zasad wydawcy o poprawnej architektury procesora. Stary zestaw zasad wydawcy nie może zrealizować używanego zestawu z zestawu ma inny procesor.  
  
     Inny konsekwencją jest, że konsolidator w wersji 2.0 nie może służyć do tworzenia zestaw zasad wydawcy dla zestawu skompilowanego za pomocą wcześniejszych wersji programu .NET Framework, ponieważ określa ona zawsze architektury procesora.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Dodawanie zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów  
 Użyj [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów  
  
1.  Wpisz następujące polecenie w wierszu polecenia:  
  
     **gacutil /i***publisherPolicyAssemblyFile*   
  
     Następujące polecenie dodaje `policy.1.0.myAssembly.dll` do globalnej pamięci podręcznej zestawów.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  Nie można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów, chyba że oryginalnego pliku zasad wydawcy znajduje się w tym samym katalogu co zestaw.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)  
 [Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md)

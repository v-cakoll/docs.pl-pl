---
title: 'Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: dedf5ab51ab5cf9befb5bd183968388406df4e5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181460"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework
Aktywacja bez rejestracji dla składników opartych na platformie .NET Framework jest tylko nieco bardziej skomplikowana niż w przypadku składników COM. Konfiguracja wymaga dwóch manifestów:  
  
- Aplikacje COM muszą mieć manifest aplikacji w stylu Win32, aby zidentyfikować składnik zarządzany.  
  
- Składniki oparte na platformie .NET Framework muszą mieć manifest składnika dla informacji aktywacji potrzebnych w czasie wykonywania.  
  
 W tym temacie opisano sposób skojarzenia manifestu aplikacji z aplikacją; skojarzyć manifest komponentu ze składnikiem; i osadź manifest komponentu w złożeniu.  
  
### <a name="to-create-an-application-manifest"></a>Aby utworzyć manifest aplikacji  
  
1. Za pomocą edytora XML utwórz (lub zmodyfikuj) manifest aplikacji należący do aplikacji COM, który współpracuje z co najmniej jednym składnikiem zarządzanym.  
  
2. Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Aby uzyskać informacje o elementach manifestu i ich [atrybutach,](/windows/desktop/SbsCs/application-manifests)zobacz Manifesty aplikacji .  
  
3. Zidentyfikuj właściciela manifestu. W poniższym `myComApp` przykładzie wersja 1 jest właścicielem pliku manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />  
    ```  
  
4. Identyfikowanie zestawów zależnych. W poniższym `myComApp` przykładzie `myManagedComp`zależy od .  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. Zapisz i nazwij plik manifestu. Nazwa manifestu aplikacji jest nazwą pliku wykonywalnego zestawu, po którym następuje rozszerzenie .manifest. Na przykład nazwa pliku manifestu aplikacji dla myComApp.exe to myComApp.exe.manifest.  
  
 Manifest aplikacji można zainstalować w tym samym katalogu co aplikacja COM. Alternatywnie można dodać go jako zasób do pliku .exe aplikacji. Aby uzyskać dodatkowe informacje, Aby uzyskać więcej informacji, zobacz [Informacje o złożeniach obok siebie](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Aby utworzyć manifest komponentu  
  
1. Za pomocą edytora XML utwórz manifest składnika, aby opisać zarządzany zestaw.  
  
2. Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Zidentyfikuj właściciela pliku. Element `<assemblyIdentity>` `<dependentAssembly>` elementu w pliku manifestu aplikacji musi być zgodny z elementem manifestu składnika. W poniższym `myManagedComp` przykładzie wersja 1.2.3.4 jest właścicielem pliku manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. Zidentyfikuj każdą klasę w zestawie. Użyj `<clrClass>` elementu, aby jednoznacznie zidentyfikować każdą klasę w zestawie zarządzanym. Element, który jest podśrodkiem `<assembly>` elementu, ma atrybuty opisane w poniższej tabeli.  
  
    |Atrybut|Opis|Wymagany|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identyfikator, który określa klasę, która ma zostać aktywowana.|Tak|  
    |`description`|Ciąg, który informuje użytkownika o składniku. Pusty ciąg jest wartością domyślną.|Nie|  
    |`name`|Ciąg reprezentujący klasę zarządzaną.|Tak|  
    |`progid`|Identyfikator, który ma być używany do aktywacji z późnym użyciem.|Nie|  
    |`threadingModel`|Model gwintowania COM. "Oba" jest wartością domyślną.|Nie|  
    |`runtimeVersion`|Określa wersję wspólnego środowiska wykonawczego języka (CLR) do użycia. Jeśli ten atrybut nie zostanie określony, a program CLR nie jest jeszcze załadowany, składnik jest ładowany z najnowszym zainstalowanym programem CLR przed programem CLR w wersji 4. Jeśli określisz v1.0.3705, v1.1.4322 lub v2.0.50727, wersja automatycznie przekieruje do najnowszej zainstalowanej wersji CLR przed CLR w wersji 4 (zwykle v2.0.50727). Jeśli inna wersja CLR jest już załadowany i określoną wersję można załadować obok siebie w procesie, określona wersja jest ładowany; w przeciwnym razie używany jest załadowany clr. Może to spowodować awarię obciążenia.|Nie|  
    |`tlbid`|Identyfikator biblioteki typów zawierający informacje o typie klasy.|Nie|  
  
     We wszystkich tagach atrybutów rozróżniana jest wielkość liter. Można uzyskać clsids, progids, modele wątków i wersji środowiska wykonawczego, wyświetlając eksportowane biblioteki typów dla zestawu z OLE/COM ObjectViewer (Oleview.exe).  
  
     Poniższy manifest składnika identyfikuje `testClass1` `testClass2`dwie klasy i .  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. Zapisz i nazwij plik manifestu. Nazwa manifestu składnika jest nazwą biblioteki zestawu, po której następuje rozszerzenie manifestu. Na przykład myManagedComp.dll jest myManagedComp.manifest.  
  
 Manifest komponentu należy osadzić jako zasób w złożeniu.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Aby osadzić manifest komponentu w zestawie zarządzanym  
  
1. Utwórz skrypt zasobu zawierający następującą instrukcję:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     W tej `myManagedComp.manifest` instrukcji jest nazwa manifestu składnika są osadzone. W tym przykładzie nazwa `myresource.rc`pliku skryptu to .  
  
2. Skompiluj skrypt przy użyciu kompilatora zasobów systemu Microsoft Windows (Rc.exe). W wierszu polecenia wpisz następujące polecenie:  
  
     `rc myresource.rc`  
  
     Program Rc.exe `myresource.res` tworzy plik zasobu.  
  
3. Skompiluj ponownie plik źródłowy zestawu i określ plik zasobu za pomocą opcji **/win32res:**  
  
    `/win32res:myresource.res`  
  
     Ponownie, `myresource.res` jest nazwa pliku zasobów zawierającego zasoby osadzone.  
  
## <a name="see-also"></a>Zobacz też

- [Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)
- [Wymagania dotyczące rejestracji-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurowanie składników COM do aktywacji bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Rejestracja-Free Aktywacja . Składniki oparte na sieci: przewodnik](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))

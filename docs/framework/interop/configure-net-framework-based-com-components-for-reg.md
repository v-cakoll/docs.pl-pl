---
title: 'Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8f78e926835e86fdc20da5e4e1bc66c4b6ab1a2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625450"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework
Aktywacji bez rejestracji dla składników opartych na programie .NET Framework jest tylko nieco bardziej skomplikowane niż jest dla składników COM. Instalator wymaga dwóch manifesty:  
  
- Aplikacje COM musi mieć Win32 stylu manifest aplikacji, aby zidentyfikować zarządzanego składnika.  
  
- Składniki .NET framework, musi mieć manifestu składnika, aby uzyskać informacje o aktywacji potrzebnych w czasie wykonywania.  
  
 W tym temacie opisano, jak skojarzyć manifest aplikacji za pomocą aplikacji; Kojarzenie manifestu składnika za pomocą składnika; i osadzanie manifestu składnika w zestawie.  
  
### <a name="to-create-an-application-manifest"></a>Aby utworzyć manifest aplikacji  
  
1. Za pomocą edytora XML, Utwórz (lub zmodyfikuj) należące do aplikacji modelu COM, który jest współdziałanie z co najmniej jednego składnika zarządzanego manifest aplikacji.  
  
2. Wstaw następujący nagłówek standardowy na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Aby uzyskać informacji na temat ich atrybuty i elementy manifestu, zobacz [manifesty aplikacji](/windows/desktop/SbsCs/application-manifests).  
  
3. Określ właściciela manifestu. W poniższym przykładzie `myComApp` w wersji 1 jest właścicielem pliku manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. Zidentyfikuj zestawów zależnych. W poniższym przykładzie `myComApp` zależy od `myManagedComp`.  
  
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
  
5. Zapisz i nazwa pliku manifestu. Nazwa manifest aplikacji jest nazwa zestawu pliku wykonywalnego, następuje rozszerzenie .manifest. Na przykład nazwa pliku manifestu aplikacji dla myComApp.exe jest myComApp.exe.manifest.  
  
 W tym samym katalogu co aplikacji modelu COM, można zainstalować manifest aplikacji. Alternatywnie można go dodać jako zasób do pliku .exe aplikacji. Aby uzyskać dodatkowe informacje, aby uzyskać więcej informacji, zobacz [informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Aby utworzyć manifest składnika  
  
1. Za pomocą edytora XML, Utwórz manifestu składnika, aby opisać zarządzanego zestawu.  
  
2. Wstaw następujący nagłówek standardowy na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Określ właściciela pliku. `<assemblyIdentity>` Elementu `<dependentAssembly>` elementu w pliku manifestu aplikacji musi pasować do w manifeście składnika. W poniższym przykładzie `myManagedComp` wersję 1.2.3.4 właścicielem pliku manifestu.  
  
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
  
4. Zidentyfikuj każdej klasy w zestawie. Użyj `<clrClass>` element do unikatowego identyfikowania każdej klasy w zestawie zarządzanym. Element, który jest podelementem z `<assembly>` elementu atrybutami opisane w poniższej tabeli.  
  
    |Atrybut|Opis|Wymagane|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identyfikator, który określa klasę do aktywacji.|Tak|  
    |`description`|Ciąg, który informuje użytkownika o informacje o składniku. Pusty ciąg jest ustawieniem domyślnym.|Nie|  
    |`name`|Ciąg, który reprezentuje klasy zarządzanej.|Tak|  
    |`progid`|Identyfikator, który ma być używany do aktywacji z późnym wiązaniem.|Nie|  
    |`threadingModel`|Model wątkowości COM. "Both" jest wartością domyślną.|Nie|  
    |`runtimeVersion`|Wersja wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) do użycia. Jeśli nie określisz tego atrybutu, a środowisko CLR nie jest już załadowany, składnik jest ładowany z najnowsza wersja zainstalowanego środowiska CLR przed CLR w wersji 4. Jeśli określisz v1.0.3705, v1.1.4322 lub v2.0.50727 wersję automatycznie przenosi do przodu do najnowszej zainstalowanej wersji środowiska CLR przed CLR w wersji 4 (zazwyczaj v2.0.50727). Jeśli inna wersja środowiska CLR jest już załadowany, określonej wersji, może zostać załadowany side-by-side w procesie jest ładowany określonej wersji; w przeciwnym razie załadowane środowisko CLR jest używany. Może to spowodować awarię obciążenia.|Nie|  
    |`tlbid`|Identyfikator biblioteki typów, zawierający informacje o typie o klasie.|Nie|  
  
     Wszystkie tagi atrybutów jest rozróżniana wielkość liter. Możesz uzyskać CLSID ProgID, Modele wątkowości i wersji środowiska uruchomieniowego, wyświetlając wyeksportowanej biblioteki typów dla zestawu z ObjectViewer OLE/COM (Oleview.exe).  
  
     Następujące manifestu składnika identyfikuje dwóch klas `testClass1` i `testClass2`.  
  
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
  
5. Zapisz i nazwa pliku manifestu. Nazwa manifestu składnika jest nazwa biblioteki zestawu, a po nim rozszerzenie .manifest. Na przykład myManagedComp.dll jest myManagedComp.manifest.  
  
 Manifestu składnika należy osadzić jako zasób w zestawie.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Osadzanie manifestu składnika w zestaw zarządzany  
  
1. Utwórz skrypt zasobu, który zawiera następującą instrukcję:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     W niniejszych zasadach `myManagedComp.manifest` nazywa się manifestu składnika osadzona. W tym przykładzie jest nazwa pliku skryptu `myresource.rc`.  
  
2. Kompiluj skrypt z użyciem Microsoft Windows Resource Compiler (Rc.exe). W wierszu polecenia wpisz następujące polecenie:  
  
     `rc myresource.rc`  
  
     Tworzy RC.exe `myresource.res` pliku zasobów.  
  
3. Ponownie skompiluj plik źródłowy zestawu i określ plik zasobów przy użyciu **/win32res** opcji:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Ponownie `myresource.res` to nazwa pliku zasobu zawierającego osadzonego zasobu.  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)
- [Wymagania dotyczące współdziałania z modelem COM bez rejestrowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurowanie składników COM na potrzeby aktywacji bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Współdziałanie aktywacji. NET składników: Przewodnik](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))

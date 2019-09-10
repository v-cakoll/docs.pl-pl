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
ms.openlocfilehash: baabff187fb8a22aea37c4fb4c1dc11a680d3bb8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70853852"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework
Aktywacja bez rejestracji dla składników opartych na .NET Framework jest nieco bardziej skomplikowana niż w przypadku składników modelu COM. Instalator wymaga dwóch manifestów:  
  
- Aplikacje COM muszą mieć manifest aplikacji w stylu Win32, aby zidentyfikować składnik zarządzany.  
  
- Składniki oparte na .NET Framework muszą mieć manifest składnika dla informacji o aktywacji wymaganych w czasie wykonywania.  
  
 W tym temacie opisano sposób kojarzenia manifestu aplikacji z aplikacją; Skojarz manifest składnika ze składnikiem; i osadzić Manifest składnika w zestawie.  
  
### <a name="to-create-an-application-manifest"></a>Aby utworzyć manifest aplikacji  
  
1. Za pomocą edytora XML Utwórz (lub zmodyfikuj) manifest aplikacji należący do aplikacji COM, która współdziała z co najmniej jednym zarządzanym składnikiem.  
  
2. Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Aby uzyskać informacje na temat elementów manifestu i ich atrybutów, zobacz [manifesty aplikacji](/windows/desktop/SbsCs/application-manifests).  
  
3. Zidentyfikuj właściciela manifestu. W poniższym przykładzie `myComApp` wersja 1 jest właścicielem pliku manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. Zidentyfikuj zestawy zależne. W poniższym przykładzie `myComApp` zależy od `myManagedComp`.  
  
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
  
5. Zapisz plik manifestu i nadaj mu nazwę. Nazwa manifestu aplikacji jest nazwą pliku wykonywalnego zestawu, po którym następuje rozszerzenie. manifest. Na przykład nazwa pliku manifestu aplikacji dla myComApp. exe to myComApp. exe. manifest.  
  
 Manifest aplikacji można zainstalować w tym samym katalogu, w którym znajduje się aplikacja COM. Alternatywnie możesz dodać go jako zasób do pliku. exe aplikacji. Aby uzyskać dodatkowe informacje, zobacz [Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-).  
  
#### <a name="to-create-a-component-manifest"></a>Aby utworzyć manifest składnika  
  
1. Za pomocą edytora XML Utwórz manifest składnika, aby opisać zarządzany zestaw.  
  
2. Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. Zidentyfikuj właściciela pliku. `<assemblyIdentity>` Element`<dependentAssembly>` elementu w pliku manifestu aplikacji musi być zgodny z elementem w manifeście składnika. W poniższym przykładzie `myManagedComp` wersja 1.2.3.4 jest właścicielem pliku manifestu.  
  
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
  
4. Zidentyfikuj każdą klasę w zestawie. Użyj elementu `<clrClass>` , aby jednoznacznie identyfikować każdą klasę w zarządzanym zestawie. Element, który jest podelementem `<assembly>` elementu, ma atrybuty opisane w poniższej tabeli.  
  
    |Atrybut|Opis|Wymagane|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identyfikator określający klasę, która ma zostać aktywowana.|Tak|  
    |`description`|Ciąg, który informuje użytkownika o składniku. Pusty ciąg jest wartością domyślną.|Nie|  
    |`name`|Ciąg, który reprezentuje klasę zarządzaną.|Tak|  
    |`progid`|Identyfikator, który ma być używany w przypadku aktywacji z późnym wiązaniem.|Nie|  
    |`threadingModel`|Model wątkowości COM. Wartość domyślna to "Both".|Nie|  
    |`runtimeVersion`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do użycia. Jeśli nie określisz tego atrybutu, a środowisko CLR nie jest już załadowane, składnik zostanie załadowany z najnowszym zainstalowanym środowiskiem CLR przed środowiskiem CLR w wersji 4. W przypadku określenia v 1.0.3705, v 1.1.4322 lub v 2.0.50727 wersja zostanie automatycznie przesunięta do najnowszej zainstalowanej wersji środowiska CLR przed środowiskiem CLR w wersji 4 (zazwyczaj 2.0.50727). Jeśli inna wersja środowiska CLR jest już załadowana i określona wersja może zostać załadowana równolegle, określona wersja zostanie załadowana. w przeciwnym razie zostanie użyte załadowane środowisko CLR. Może to spowodować niepowodzenie ładowania.|Nie|  
    |`tlbid`|Identyfikator biblioteki typów, który zawiera informacje o typie klasy.|Nie|  
  
     We wszystkich tagach atrybutów jest rozróżniana wielkość liter. Możesz uzyskać identyfikatory CLSID, ProgID, modele wątkowości i wersję środowiska uruchomieniowego, wyświetlając eksportowaną bibliotekę typów dla zestawu za pomocą OLE/COM ObjectViewer (OleView. exe).  
  
     Następujący manifest składnika identyfikuje dwie klasy `testClass1` i. `testClass2`  
  
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
  
5. Zapisz plik manifestu i nadaj mu nazwę. Nazwa manifestu składnika jest nazwą biblioteki zestawu, po której następuje rozszerzenie. manifest. Na przykład myManagedComp. dll to myManagedComp. manifest.  
  
 Manifest składnika należy osadzić jako zasób w zestawie.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Aby osadzić Manifest składnika w zarządzanym zestawie  
  
1. Utwórz skrypt zasobów zawierający następującą instrukcję:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     W tej instrukcji jest `myManagedComp.manifest` nazwą manifestu składnika, który jest osadzony. W tym przykładzie nazwa pliku skryptu to `myresource.rc`.  
  
2. Skompiluj skrypt przy użyciu kompilatora zasobów systemu Microsoft Windows (RC. exe). W wierszu polecenia wpisz następujące polecenie:  
  
     `rc myresource.rc`  
  
     RC. exe tworzy `myresource.res` plik zasobów.  
  
3. Skompiluj ponownie plik źródłowy zestawu i określ plik zasobów przy użyciu opcji **/win32res** :  
  
    `/win32res:myresource.res`  
  
     `myresource.res` Ponownie jest nazwą pliku zasobów zawierającego osadzone zasoby.  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)
- [Wymagania dotyczące międzyoperacyjności modelu COM bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [Konfigurowanie składników COM do aktywacji bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [Aktywacja bez rejestracji. Składniki oparte na sieci: Przewodnik](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392856"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework
Aktywacja bez rejestrowania dla składników opartych na programie .NET Framework jest tylko nieco bardziej skomplikowane niż dla składników COM. Instalator wymaga dwóch manifestów:  
  
-   Aplikacje COM musi mieć manifest aplikacji Win32 stylu, aby zidentyfikować zarządzanego składnika.  
  
-   Składniki platformy .NET framework musi mieć manifestu składnika Aktywacja informacji wymaganych w czasie wykonywania.  
  
 W tym temacie opisano, jak skojarzyć manifest aplikacji przy użyciu aplikacji; Skojarz manifestu składnika ze składnikiem; i osadzania manifestu składnika w zestawie.  
  
### <a name="to-create-an-application-manifest"></a>Aby utworzyć manifestu aplikacji  
  
1.  Przy użyciu edytora XML, utworzyć lub zmodyfikować należące do aplikacji modelu COM, który jest współdziałanie z jednego lub więcej składników zarządzanych manifest aplikacji.  
  
2.  Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Aby uzyskać informacji na temat elementów manifestu i ich atrybutów, zobacz [manifesty aplikacji](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).  
  
3.  Określ właściciela manifestu. W poniższym przykładzie `myComApp` wersji 1 jest właścicielem pliku manifestu.  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Zidentyfikuj zestawów zależnych. W poniższym przykładzie `myComApp` zależy od `myManagedComp`.  
  
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
  
5.  Zapisz i nazwa pliku manifestu. Nazwa manifest aplikacji jest nazwa pliku wykonywalnego zestawu następuje rozszerzenia manifest. Na przykład nazwa pliku manifestu aplikacji dla myComApp.exe jest myComApp.exe.manifest.  
  
 W tym samym katalogu co aplikacji modelu COM, należy zainstalować manifest aplikacji. Alternatywnie można go dodać jako zasób do pliku .exe aplikacji. Aby uzyskać dodatkowe informacje, aby uzyskać więcej informacji, zobacz [informacje o zestawach Side-by-Side](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).  
  
#### <a name="to-create-a-component-manifest"></a>Aby utworzyć manifestu składnika  
  
1.  Przy użyciu edytora XML, tworzenie manifestu składnika do opisywania zarządzanego zestawu.  
  
2.  Wstaw następujący standardowy nagłówek na początku pliku:  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Określ właściciela pliku. `<assemblyIdentity>` Elementu `<dependentAssembly>` elementu w pliku manifestu aplikacji musi odpowiadać nazwie w manifeście składnika. W poniższym przykładzie `myManagedComp` wersji 1.2.3.4 właścicielem pliku manifestu.  
  
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
  
4.  Zidentyfikuj każda klasa w zestawie. Użyj `<clrClass>` elementu, aby jednoznacznie zidentyfikować każda klasa w zarządzanych zestawów. Element, który jest podelementem z `<assembly>` elementu z atrybutami opisane w poniższej tabeli.  
  
    |Atrybut|Opis|Wymagane|  
    |---------------|-----------------|--------------|  
    |`clsid`|Identyfikator, który określa klasę do aktywacji.|Tak|  
    |`description`|Ciąg, który informuje użytkownika o składnika. Ciąg pusty jest ustawieniem domyślnym.|Nie|  
    |`name`|Ciąg, który reprezentuje zarządzanej klasy.|Tak|  
    |`progid`|Identyfikator służący do aktywacji z późnym wiązaniem.|Nie|  
    |`threadingModel`|Model wątkowości COM. "Both" jest wartością domyślną.|Nie|  
    |`runtimeVersion`|Określa wersję środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego do użycia. Jeśli ten atrybut nie zostanie określony, a środowisko CLR nie jest już załadowany, składnik jest załadowana najnowsza wersja zainstalowanego środowiska CLR przed CLR w wersji 4. Jeśli określisz v1.0.3705, v1.1.4322 lub v2.0.50727 wersja automatycznie przedstawia do przodu najnowsza wersja zainstalowana wersja CLR przed CLR w wersji 4 (zazwyczaj v2.0.50727). Jeśli określona wersja może zostać załadowany side-by-side w trakcie innej wersji środowiska CLR został już załadowany, jest ładowany określonej wersji; w przeciwnym razie jest używana załadować środowiska CLR. Może to spowodować błąd ładowania.|Nie|  
    |`tlbid`|Identyfikator biblioteki typów, zawierający typ informacji o klasie.|Nie|  
  
     Wszystkie tagi atrybutu jest rozróżniana wielkość liter. Możesz uzyskać CLSID ProgID, wątkowość modeli i wersja środowiska uruchomieniowego, wyświetlając wyeksportowanej biblioteki typów dla zestawu z ObjectViewer OLE/COM (Oleview.exe).  
  
     Następujące manifestu składnika identyfikuje dwie klasy `testClass1` i `testClass2`.  
  
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
  
5.  Zapisz i nazwa pliku manifestu. Nazwa manifestu składnika jest nazwa biblioteki zestawu, a po nim rozszerzenie manifest. Na przykład myManagedComp.dll jest myManagedComp.manifest.  
  
 Należy osadzić manifestu składnika jako zasób w zestawie.  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>Osadzanie manifestu składnika w zarządzanych zestawów  
  
1.  Utwórz skrypt zasobu, który zawiera następująca instrukcja:  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     W tej instrukcji `myManagedComp.manifest` to nazwa manifestu składnika osadzona. Na przykład nazwa pliku skryptu jest `myresource.rc`.  
  
2.  Kompilacja skryptu, za pomocą kompilatora zasobów systemu Windows firmy Microsoft (Rc.exe). W wierszu polecenia wpisz następujące polecenie:  
  
     `rc myresource.rc`  
  
     Tworzy RC.exe `myresource.res` pliku zasobu.  
  
3.  Ponownie skompiluj plik źródłowy zestawu i określ plik zasobów za pomocą **/win32res** opcji:  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     Ponownie `myresource.res` to nazwa pliku zasobu zawierającego osadzony zasób.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z COM bez rejestrowania](registration-free-com-interop.md)  
 [Wymagania dotyczące współdziałanie z COM bez rejestrowania](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))  
 [Konfigurowanie aktywacji bez rejestracji składników COM](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))  
 [Aktywacja bez rejestrowania programu. Składników opartych na sieci: Wskazówki](https://msdn.microsoft.com/library/ms973915.aspx)

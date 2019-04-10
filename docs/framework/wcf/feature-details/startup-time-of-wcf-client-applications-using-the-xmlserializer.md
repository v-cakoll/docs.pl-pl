---
title: 'Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b6f010cb5edc3111f05c78f5d27cf178bd501ef9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326427"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer
Usługi i aplikacje klienckie, które używają typów danych, które są możliwe do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może skutkować wydajności uruchamiania powolne.  
  
> [!NOTE]
>  Serializacja wstępnie wygenerowanego kodu należy używać tylko w aplikacjach klienckich, a nie w usługach.  
  
 [Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji, generowania kodu serializacji niezbędne z skompilowanych zestawów dla aplikacji. Svcutil.exe generuje kod serializacji dla wszystkich typów danych używane w kontraktach usług w zestawie skompilowanej aplikacji, który może być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer>. Kontrakty usługi i operacji, korzystających z <xref:System.Xml.Serialization.XmlSerializer> są oznaczone <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Do generowania kodu serializacji elementu XmlSerializer  
  
1. Skompilować kod usługi lub klienta do jednego lub więcej zestawów.  
  
2. Otwórz wiersz polecenia zestawu SDK.  
  
3. W wierszu polecenia Uruchom narzędzia Svcutil.exe w następującym formacie.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi. Svcutil.exe generuje kod serializacji dla wszystkich typów danych używane w kontraktach usług w zestawie skompilowanej aplikacji, który może być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe może generować jedynie C# kodu serializacji. Jeden plik kodu źródłowego jest generowany dla każdego zestawu danych wejściowych. Nie można użyć **/language** przełącznik, aby zmienić język generowanego kodu.  
  
     Aby określić ścieżkę do zestawów zależnych, użyj **/reference** opcji.  
  
4. Udostępnij kodu wygenerowanego serializacji do aplikacji przy użyciu jednej z następujących opcji:  
  
    1.  Kompilowanie kodu wygenerowanego serializacji w osobnym zestawie o nazwie [*oryginalny zestaw*]. XmlSerializers.dll (na przykład MyApp.XmlSerializers.dll). Aplikacja musi umożliwiać można załadować zestawu, który musi być podpisany przy użyciu tego samego klucza jako oryginalnego zestawu. Jeśli oryginalny zestaw zostanie ponownie skompilowany, należy ponownie wygenerować zestawu serializacji.  
  
    2.  Kompilowanie kodu wygenerowanego serializacji w osobnym zestawie i użyj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> na kontrakt usługi, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ustaw <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości, aby wskazywał zestawu skompilowanego serializacji.  
  
    3.  Kompilowanie kodu wygenerowanego serializacji do swojego zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> umową serwisową, który używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nie należy ustawiać <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości. Domyślny zestaw serializacji zakłada się, że bieżący zestaw.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Do generowania kodu serializacji elementu XmlSerializer w programie Visual Studio  
  
1. Tworzenie usługi i klienta WCF projektów w programie Visual Studio. Następnie dodaj odwołanie do usługi do projektu klienta.  
  
2. Dodaj <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi *reference.cs* pliku w projekcie aplikacji klienckich, w obszarze **serviceReference** -> **reference.svcmap** . Należy zauważyć, że należy do wyświetlenia wszystkich plików w **Eksploratora rozwiązań** aby te pliki.  
  
3. Tworzenie aplikacji klienckiej.  
  
4. Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia wstępnie wygenerowanego serializatora *.cs* pliku przy użyciu polecenia:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Argument Ścieżkazestawu Określa ścieżkę do zestawu klienta programu WCF.  
  
     Przykład:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* zostanie wygenerowany plik.  
  
5. Skompiluj zestaw wstępnie wygenerowanego serializacji.  
  
     Na podstawie przykładu w poprzednim kroku, polecenie compile będzie następująca:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Sprawdź wygenerowany *WCFClient.XmlSerializers.dll* znajduje się w tym samym katalogu co aplikacja klienta, która jest *WCFClient.exe* w tym przypadku.  
  
6. Uruchom aplikację kliencką w zwykły sposób. Zestaw serializacji wstępnie wygenerowanego będą używane.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje typy serializacji dla `XmlSerializer` typy, które każda usługa umów z użyciem zestawu.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

---
title: 'Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: f8766a5dfa2bcfc715a0f0e21274f7c6ac04ad15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944893"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer
Usługi i aplikacje klienckie korzystające z typów danych, które można serializować <xref:System.Xml.Serialization.XmlSerializer> przy użyciu generowania i kompilowania kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować spowolnienie wydajności.  
  
> [!NOTE]
> Wstępnie wygenerowany kod serializacji może być używany tylko w aplikacjach klienckich, a nie w usługach.  
  
 [Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może zwiększyć wydajność uruchamiania tych aplikacji, generując wymagany kod serializacji z skompilowanych zestawów dla aplikacji. Svcutil. exe generuje kod serializacji dla wszystkich typów danych używanych w kontraktach usług w skompilowanym zestawie aplikacji, który może być serializowany przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Kontrakty <xref:System.Xml.Serialization.XmlSerializer> usługi i operacji używające są oznaczone <xref:System.ServiceModel.XmlSerializerFormatAttribute>za pomocą.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Aby wygenerować kod serializacji XmlSerializer  
  
1. Skompiluj kod usługi lub klienta w jednym lub kilku zestawach.  
  
2. Otwórz wiersz polecenia zestawu SDK.  
  
3. W wierszu polecenia Uruchom narzędzie Svcutil. exe, używając następującego formatu.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi. Svcutil. exe generuje kod serializacji dla wszystkich typów danych używanych w kontraktach usług w skompilowanym zestawie aplikacji, który może być serializowany przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil. exe może generować C# tylko kod serializacji. Dla każdego zestawu wejściowego jest generowany jeden plik kodu źródłowego. Nie można użyć przełącznika **/Language** , aby zmienić język wygenerowanego kodu.  
  
     Aby określić ścieżkę do zestawów zależnych, użyj opcji **/Reference** .  
  
4. Udostępnij wygenerowany kod serializacji aplikacji przy użyciu jednej z następujących opcji:  
  
    1. Kompiluj wygenerowany kod serializacji w osobnym zestawie o nazwie [*oryginalny zestaw*]. XmlSerializers. dll (na przykład MojaApl. XmlSerializers. dll). Aplikacja musi być w stanie załadować zestaw, który musi być podpisany przy użyciu tego samego klucza co oryginalny zestaw. W przypadku ponownej kompilacji oryginalnego zestawu należy ponownie wygenerować zestaw serializacji.  
  
    2. Skompiluj wygenerowany kod serializacji do oddzielnego zestawu i użyj programu <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> w ramach kontraktu usługi, który <xref:System.ServiceModel.XmlSerializerFormatAttribute>używa. Ustaw właściwości <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> , aby wskazywały skompilowany zestaw serializacji.  
  
    3. Skompiluj wygenerowany kod serializacji do zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do kontraktu usługi, który <xref:System.ServiceModel.XmlSerializerFormatAttribute>używa. Nie ustawiaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ani <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości. Przyjęto, że domyślny zestaw serializacji jest bieżącym zestawem.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Aby wygenerować kod serializacji XmlSerializer w programie Visual Studio  
  
1. Utwórz usługę WCF i projekty klienta w programie Visual Studio. Następnie Dodaj odwołanie do usługi do projektu klienta.  
  
2.  -> Dodaj do kontraktu usługi w pliku Reference.cs w projekcie aplikacji klienta w obszarze ServiceReference Reference. svcmap. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Zwróć uwagę, że musisz wyświetlić wszystkie pliki w **Eksplorator rozwiązań** , aby wyświetlić te pliki.  
  
3. Utwórz aplikację kliencką.  
  
4. Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby utworzyć wstępnie wygenerowany plik serializator *. cs* przy użyciu polecenia:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Argument assemblyPath określa ścieżkę do zestawu klienta WCF.  
  
     Takie jak:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     Plik *WCFClient.XmlSerializers.dll.cs* zostanie wygenerowany.  
  
5. Kompiluj wstępnie wygenerowany zestaw serializacji.  
  
     Na podstawie przykładu w poprzednim kroku polecenie Kompiluj będzie następujące:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Upewnij się, że wygenerowane *WCFClient. XmlSerializers. dll* znajduje się w tym samym katalogu, w którym znajduje się aplikacja kliencka, w tym przypadku *WCFClient. exe* .  
  
6. Uruchom aplikację kliencką w zwykły sposób. Zostanie użyty wstępnie wygenerowany zestaw serializacji.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje typy serializacji dla `XmlSerializer` typów, które są używane przez wszystkie kontrakty usługi w zestawie.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

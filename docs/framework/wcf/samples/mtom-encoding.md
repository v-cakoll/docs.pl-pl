---
title: Kodowanie MTOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46984ea1ac08aa1128a4f32144285f590eafb6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mtom-encoding"></a><span data-ttu-id="f4ad3-102">Kodowanie MTOM</span><span class="sxs-lookup"><span data-stu-id="f4ad3-102">MTOM Encoding</span></span>
<span data-ttu-id="f4ad3-103">W przykładzie pokazano, użyj kodowania z WSHttpBinding wiadomości mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="f4ad3-104">MTOM jest mechanizm przekazywania dużych załączników binarnych z komunikatami SOAP raw bajtów, co pozwala na mniejsze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f4ad3-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4ad3-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4ad3-107">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4ad3-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="f4ad3-109">Domyślnie wysyła WSHttpBinding i odebranych komunikatów jako zwykły tekst XML.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="f4ad3-110">Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut w konfiguracji powiązania (jak poniższy przykład kodu) lub bezpośrednio za pomocą powiązania `MessageEncoding` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="f4ad3-111">Usługi lub klienta można teraz wysyłać i odbierać komunikaty MTOM.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="f4ad3-112">Koder MTOM zoptymalizować tablice bajtów i strumieni.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="f4ad3-113">W tym przykładzie używa operacji `Stream` parametru i mogą być optymalizowane.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```  
  
 <span data-ttu-id="f4ad3-114">Kontrakt wybrany dla tego przykładu przesyła dane binarne do usługi i odbiera liczba bajtów przekazany jako wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="f4ad3-115">Gdy usługa jest zainstalowana i uruchomieniu klienta, Wyświetla ilość 1000, co oznacza, że otrzymano wszystkich 1000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="f4ad3-116">W pozostałej części dane wyjściowe wyświetla listę komunikatów wersją zoptymalizowaną a niezoptymalizowaną rozmiarów różnych ładunków.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f4ad3-117">Cel przy użyciu mechanizmu MTOM jest optymalizacji transmisji dużych ładunków binarne.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="f4ad3-118">Wysyłanie wiadomości SOAP przy użyciu mechanizmu MTOM mają zauważalne narzut dla małych ładunków binarne, ale staje się doskonałe oszczędności, gdy ich wraz z upływem kilku tysięcy bajtów.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="f4ad3-119">Przyczyną tego jest czy zwykłego tekstu XML koduje dane binarne przy użyciu Base64, który wymaga cztery znaki co trzy bajtów i zwiększa rozmiar danych, jedna trzecia.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="f4ad3-120">MTOM jest w stanie przesyłać dane binarne jako nieprzetworzone bajtów, oszczędzając czas kodowanie dekodowania i co jest mniejszy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="f4ad3-121">Próg kilku tysięcy bajtów jest małe w stosunku do bieżącej firm dokumenty i zdjęcia.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4ad3-122">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="f4ad3-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f4ad3-123">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="f4ad3-124">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="f4ad3-125">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f4ad3-126">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ad3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4ad3-127">See Also</span></span>

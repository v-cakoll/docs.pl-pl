---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144386"
---
# <a name="mtom-encoding"></a><span data-ttu-id="ac3d8-102">Kodowanie MTOM</span><span class="sxs-lookup"><span data-stu-id="ac3d8-102">MTOM Encoding</span></span>
<span data-ttu-id="ac3d8-103">W tym przykładzie pokazano użycie kodowania komunikatów mechanizmu optymalizacji transmisji wiadomości (MTOM) za pomocą funkcji WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="ac3d8-104">MTOM jest mechanizmem przesyłania dużych załączników binarnych z wiadomościami SOAP jako nieprzetworzonymi bajtami, co pozwala na mniejsze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ac3d8-105">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ac3d8-106">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ac3d8-107">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ac3d8-108">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="ac3d8-109">Domyślnie plik WSHttpBinding wysyła i odbiera wiadomości jako zwykły tekst XML.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="ac3d8-110">Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut w konfiguracji powiązania (jak w poniższym `MessageEncoding` przykładowym kodzie) lub bezpośrednio na powiązanie przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="ac3d8-111">Usługa lub klient może teraz wysyłać i odbierać wiadomości MTOM.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="ac3d8-112">Koder MTOM może optymalizować tablice bajtów i strumieni.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="ac3d8-113">W tym przykładzie operacja `Stream` używa parametru i dlatego można zoptymalizować.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="ac3d8-114">Kontrakt wybrany dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę bajtów przekazanych jako wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="ac3d8-115">Po zainstalowaniu usługi i uruchomieniu klienta, drukuje liczbę 1000, co oznacza, że wszystkie 1000 bajtów zostały odebrane.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="ac3d8-116">Pozostała część danych wyjściowych zawiera zoptymalizowane i niestyptowane rozmiary komunikatów dla różnych ładunków.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
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
  
 <span data-ttu-id="ac3d8-117">Celem wykorzystania MTOM jest optymalizacja transmisji dużych ładunków binarnych.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="ac3d8-118">Wysyłanie wiadomości SOAP przy użyciu MTOM ma zauważalne obciążenie dla małych ładunków binarnych, ale staje się wielką oszczędnością, gdy rosną one ponad kilka tysięcy bajtów.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="ac3d8-119">Powodem tego jest to, że normalny tekst XML koduje dane binarne przy użyciu Base64, który wymaga czterech znaków na każde trzy bajty i zwiększa rozmiar danych o jedną trzecią.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="ac3d8-120">MTOM jest w stanie przesyłać dane binarne jako nieprzetworzone bajty, oszczędzając czas kodowania/dekodowania, a wynikowe jest mniejsze.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="ac3d8-121">Próg kilku tysięcy bajtów jest niewielki w porównaniu do dzisiejszych dokumentów biznesowych i fotografii cyfrowych.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ac3d8-122">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="ac3d8-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ac3d8-123">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ac3d8-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ac3d8-124">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac3d8-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ac3d8-125">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac3d8-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ac3d8-126">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ac3d8-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

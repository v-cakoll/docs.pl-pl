---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: ab8abdf79304037f2b4039407115a3f64a0afa4e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424071"
---
# <a name="mtom-encoding"></a><span data-ttu-id="7b571-102">Kodowanie MTOM</span><span class="sxs-lookup"><span data-stu-id="7b571-102">MTOM Encoding</span></span>
<span data-ttu-id="7b571-103">Ten przykład ilustruje użycie kodowania komunikatów mechanizmu optymalizacji transmisji wiadomości (MTOM) za pomocą WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="7b571-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="7b571-104">MTOM to mechanizm przesyłania dużych załączników binarnych przy użyciu komunikatów protokołu SOAP jako bajtów nieprzetworzonych, co pozwala na mniejsze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7b571-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b571-105">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7b571-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b571-106">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="7b571-106">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7b571-107">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b571-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b571-108">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7b571-108">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="7b571-109">Domyślnie WSHttpBinding wysyła i odbiera komunikaty jako zwykły tekst XML.</span><span class="sxs-lookup"><span data-stu-id="7b571-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="7b571-110">Aby włączyć wysyłanie i otrzymywanie komunikatów MTOM, ustaw atrybut `messageEncoding` w konfiguracji powiązania (jak w poniższym kodzie) lub bezpośrednio na powiązanie przy użyciu właściwości `MessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="7b571-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="7b571-111">Usługa lub klient mogą teraz wysyłać i odbierać komunikaty mechanizmu MTOM.</span><span class="sxs-lookup"><span data-stu-id="7b571-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="7b571-112">Koder MTOM może zoptymalizować tablice bajtów i strumieni.</span><span class="sxs-lookup"><span data-stu-id="7b571-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="7b571-113">W tym przykładzie operacja używa parametru `Stream` i w związku z tym może być zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="7b571-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="7b571-114">Umowa wybrana dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę przekazanych bajtów jako wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="7b571-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="7b571-115">Po zainstalowaniu usługi i uruchomieniu klienta program drukuje numer 1000, który wskazuje, że odebrano wszystkie 1000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="7b571-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="7b571-116">Pozostała część danych wyjściowych zawiera zoptymalizowane i niezoptymalizowane rozmiary komunikatów dla różnych ładunków.</span><span class="sxs-lookup"><span data-stu-id="7b571-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="7b571-117">Celem używania mechanizmu MTOM jest zoptymalizowanie przesyłania dużych ładunków binarnych.</span><span class="sxs-lookup"><span data-stu-id="7b571-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="7b571-118">Wysyłanie komunikatu protokołu SOAP przy użyciu mechanizmu MTOM ma zauważalne obciążenie dla małych ładunków binarnych, ale stają się doskonałym oszczędnościem, gdy rośnie w ciągu kilku tysięcy bajtów.</span><span class="sxs-lookup"><span data-stu-id="7b571-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="7b571-119">Przyczyną tego jest fakt, że zwykły tekst XML koduje dane binarne przy użyciu algorytmu Base64, który wymaga czterech znaków dla każdego z trzech bajtów i zwiększa rozmiar danych o jeden trzeci.</span><span class="sxs-lookup"><span data-stu-id="7b571-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="7b571-120">MTOM jest w stanie przesłać dane binarne jako nieprzetworzone bajty, co umożliwia zapisanie czasu kodowania/dekodowania i wygenerowanie mniejszych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7b571-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="7b571-121">Próg kilku tysięcy bajtów jest mały w porównaniu z współczesnymi dokumentami biznesowymi i fotografiami cyfrowymi.</span><span class="sxs-lookup"><span data-stu-id="7b571-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b571-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="7b571-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7b571-123">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b571-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7b571-124">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b571-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7b571-125">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b571-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7b571-126">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b571-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

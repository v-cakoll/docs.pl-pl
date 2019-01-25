---
title: Kodowanie MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 9fe278f9a85286f8067ef3a67bfbeb3cb83f984e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608796"
---
# <a name="mtom-encoding"></a><span data-ttu-id="c4dce-102">Kodowanie MTOM</span><span class="sxs-lookup"><span data-stu-id="c4dce-102">MTOM Encoding</span></span>
<span data-ttu-id="c4dce-103">Niniejszy przykład pokazuje użycie kodowania za pomocą WSHttpBinding komunikatu komunikat transmisji optymalizacji mechanizm (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c4dce-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="c4dce-104">MTOM jest mechanizm przekazywania dużych załączników binarnych za pomocą protokołu SOAP wiadomości jako bajtów raw, pozwalając na mniejsze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c4dce-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4dce-105">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c4dce-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4dce-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c4dce-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c4dce-107">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="c4dce-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4dce-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c4dce-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="c4dce-109">Domyślnie wysyła WSHttpBinding i odebrane komunikaty w postaci zwykłego tekstu XML.</span><span class="sxs-lookup"><span data-stu-id="c4dce-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="c4dce-110">Aby włączyć wysyłanie i odbieranie komunikatów MTOM, ustaw `messageEncoding` atrybut wiązania konfiguracji (jak poniższy przykład kodu) lub bezpośrednio za pomocą powiązania `MessageEncoding` właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4dce-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="c4dce-111">Usługi lub klienta mogą teraz wysyłanie i odbieranie wiadomości MTOM.</span><span class="sxs-lookup"><span data-stu-id="c4dce-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="c4dce-112">Koder MTOM można zoptymalizować tablice bajtów i strumieni.</span><span class="sxs-lookup"><span data-stu-id="c4dce-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="c4dce-113">W tym przykładzie operacja wykorzystuje `Stream` parametru i mogą być optymalizowane.</span><span class="sxs-lookup"><span data-stu-id="c4dce-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="c4dce-114">Kontrakt wybrana dla tego przykładu przesyła dane binarne do usługi i odbiera liczbę bajtów przekazany jako wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="c4dce-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="c4dce-115">Gdy usługa jest zainstalowana i klienta, wydrukowaniu liczby 1000, co oznacza, że otrzymano wszystkich 1000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="c4dce-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="c4dce-116">W pozostałej części danych wyjściowych Wyświetla listę rozmiarów zoptymalizowanych i niezoptymalizowany wiadomości różnych ładunków.</span><span class="sxs-lookup"><span data-stu-id="c4dce-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
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
  
 <span data-ttu-id="c4dce-117">Asysty MTOM ma na celu optymalizacji transmisji w trybie duży binarne ładunki.</span><span class="sxs-lookup"><span data-stu-id="c4dce-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="c4dce-118">Trwa wysyłanie komunikatu protokołu SOAP, za pomocą MTOM ma zauważalnego obciążenie dla małych binarne ładunki, ale staje się doskonałe oszczędności, gdy ich rosnąć kilka tysięcy bajtów.</span><span class="sxs-lookup"><span data-stu-id="c4dce-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="c4dce-119">Przyczyną jest, czy zwykłego tekstu XML koduje dane binarne, przy użyciu Base64, wymaga czterech znaków dla każdego z trzech bajtów, która zwiększa rozmiar danych o jedną trzecią.</span><span class="sxs-lookup"><span data-stu-id="c4dce-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="c4dce-120">MTOM jest w stanie przesyłać danych binarnych jako bajtów raw, co umożliwia zaoszczędzenie czasu kodowania dekodowanie i co jest mniejsze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c4dce-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="c4dce-121">Próg kilka tysięcy bajtów jest mały, w porównaniu do współczesnych firm dokumenty i zdjęcia.</span><span class="sxs-lookup"><span data-stu-id="c4dce-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4dce-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="c4dce-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c4dce-123">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="c4dce-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="c4dce-124">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4dce-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="c4dce-125">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4dce-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c4dce-126">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4dce-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4dce-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4dce-127">See also</span></span>

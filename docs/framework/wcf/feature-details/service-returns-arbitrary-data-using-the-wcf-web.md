---
title: 'Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 9753fbc9b333cb7e89ddc8dff030cb1f62ede23b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600364"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF
Czasami deweloperzy muszą mieć pełną kontrolę nad sposobem zwracania danych z operacji usługi. Dzieje się tak w przypadku, gdy operacja usługi musi zwrócić dane w formacie nieobsługiwanym przez WCF. W tym temacie omówiono korzystanie z modelu programowania HTTP sieci WEB w programie WCF w celu utworzenia takiej usługi. Ta usługa ma jedną operację zwracającą strumień.  
  
### <a name="to-implement-the-service-contract"></a>Aby zaimplementować kontrakt usługi  
  
1. Zdefiniuj kontrakt usługi. Kontrakt jest wywoływany `IImageServer` i ma jedną metodę o nazwie `GetImage` , która zwraca <xref:System.IO.Stream> .  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Ponieważ metoda zwraca metodę <xref:System.IO.Stream> , WCF zakłada, że operacja ma pełną kontrolę nad bajtami, które są zwracane przez operację usługi i nie ma żadnego formatowania dla zwracanych danych.  
  
2. Zaimplementuj kontrakt usługi. Kontrakt ma tylko jedną operację ( `GetImage` ). Ta metoda generuje mapę bitową, a następnie zapisuje ją <xref:System.IO.MemoryStream> w formacie in. jpg. Następnie operacja zwraca ten strumień do obiektu wywołującego.  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     Zwróć uwagę na sekundę do ostatniego wiersza kodu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Spowoduje to ustawienie nagłówka typu zawartości `"image/jpeg"` . Mimo że ten przykład pokazuje, jak zwrócić plik. jpg, można go zmodyfikować w taki sposób, aby zwracał dowolny wymagany typ danych w dowolnym formacie. Operacja musi pobierać lub generować dane, a następnie zapisywać je w strumieniu.  
  
### <a name="to-host-the-service"></a>Aby hostować usługę  
  
1. Utwórz aplikację konsolową do hostowania usługi.  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. Utwórz zmienną do przechowywania adresu podstawowego dla usługi w ramach `Main` metody.  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie dla usługi określające klasę usługi i adres podstawowy.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Dodaj punkt końcowy przy użyciu <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otwórz hosta usługi.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć działanie usługi.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Aby wywołać usługę nieprzetworzoną przy użyciu programu Internet Explorer  
  
1. Uruchom usługę, dlatego następujące dane wyjściowe powinny zostać wyświetlone w usłudze. `Service is running Press ENTER to close the host`  
  
2. Otwórz program Internet Explorer i wpisz `http://localhost:8000/Service/GetImage?width=50&height=40` żółty prostokąt z niebieską ukośną linią w środku.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletna lista kodu dla tego tematu.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Podczas kompilowania przykładowego odwołania do kodu system. ServiceModel. dll i system. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)

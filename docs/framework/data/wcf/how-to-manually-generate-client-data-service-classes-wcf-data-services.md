---
title: 'Instrukcje: Generuj ręcznie klasy usługi danych klienta (Usługi danych programu WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 106f1cedb33c0c1b333df0b9f2b8c2a70d458a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790425"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Instrukcje: Generuj ręcznie klasy usługi danych klienta (Usługi danych programu WCF)
Usługi danych programu WCF integruje się z programem Visual Studio, aby umożliwić automatyczne generowanie klas usługi danych klienta w przypadku używania okna dialogowego **Dodaj odwołanie do usługi** do dodawania odwołania do usługi danych w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie](how-to-add-a-data-service-reference-wcf-data-services.md)do usługi danych. Można również ręcznie generować te same klasy usługi danych klienta przy użyciu narzędzia `DataSvcUtil.exe`do generowania kodu. To narzędzie, które jest dołączone do Usługi danych programu WCF, generuje klasy .NET Framework z definicji usługi danych. Można go również użyć do wygenerowania klas usługi danych z pliku modelu koncepcyjnego (. csdl) i pliku edmx, który reprezentuje model Entity Framework w projekcie programu Visual Studio.

 W przykładzie w tym temacie opisano tworzenie klas usługi danych klienta na podstawie przykładowej usługi danych Northwind. Ta usługa jest tworzona po zakończeniu [usługi danych programu WCF przewodnika Szybki Start](quickstart-wcf-data-services.md). Niektóre przykłady w tym temacie wymagają pliku modelu koncepcyjnego dla modelu Northwind. Aby uzyskać więcej informacji, zobacz [jak: Użyj programu EdmGen. exe, aby wygenerować model i pliki](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)mapowania. Niektóre przykłady w tym temacie wymagają pliku. edmx dla modelu Northwind. Aby uzyskać więcej informacji, zobacz [plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Aby wygenerować C# klasy obsługujące powiązanie danych

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Należy zastąpić wartość dostarczoną do `/uri:` parametru identyfikatorem URI wystąpienia przykładowej usługi danych Northwind.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Aby wygenerować klasy Visual Basic obsługujące powiązanie danych

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Należy zastąpić wartość dostarczoną do `/uri:` parametru identyfikatorem URI wystąpienia przykładowej usługi danych Northwind.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Aby wygenerować C# klasy oparte na identyfikatorze URI usługi

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Należy zastąpić wartość dostarczoną do `/uri:` parametru identyfikatorem URI wystąpienia przykładowej usługi danych Northwind.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Aby wygenerować klasy Visual Basic na podstawie identyfikatora URI usługi

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > Należy zastąpić wartość dostarczoną do `/uri:` parametru identyfikatorem URI wystąpienia przykładowej usługi danych Northwind.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Aby wygenerować C# klasy na podstawie pliku modelu koncepcyjnego (CSDL)

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Aby wygenerować klasy Visual Basic na podstawie pliku modelu koncepcyjnego (CSDL)

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Aby wygenerować C# klasy na podstawie pliku. edmx

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Aby wygenerować klasy Visual Basic na podstawie pliku. edmx

- W wierszu polecenia wykonaj następujące polecenie bez podziałów wierszy:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Zobacz także

- [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)
- [Instrukcje: Dodawanie odwołania do usługi danych](how-to-add-a-data-service-reference-wcf-data-services.md)
- [Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)](wcf-data-service-client-utility-datasvcutil-exe.md)

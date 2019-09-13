---
title: 'Przewodnik: Tworzenie aplikacji kryptograficznej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee6dafa8578c59d23908bf0e184091bb4ceaeb45
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895288"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Przewodnik: Tworzenie aplikacji kryptograficznej
W tym instruktażu pokazano, jak szyfrować i odszyfrowywać zawartość. Przykłady kodu są przeznaczone dla aplikacji Windows Forms. Ta aplikacja nie pokazuje rzeczywistych scenariuszy, takich jak korzystanie z kart inteligentnych. Zamiast tego pokazuje podstawowe informacje dotyczące szyfrowania i odszyfrowywania.  
  
 W tym instruktażu zastosowano następujące wytyczne dotyczące szyfrowania:  
  
- Użyj klasy, algorytmu symetrycznego, aby szyfrować i odszyfrowywać dane przy użyciu automatycznie wygenerowanego <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A>i. <xref:System.Security.Cryptography.RijndaelManaged>  
  
- Użyj algorytmu asymetrycznego, aby szyfrować i odszyfrowywać klucz do danych szyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>program. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Algorytmy asymetryczne najlepiej używać w przypadku mniejszych ilości danych, takich jak klucz.  
  
    > [!NOTE]
    > Jeśli chcesz chronić dane na komputerze zamiast wymieniać zaszyfrowaną zawartość z innymi osobami, rozważ użycie <xref:System.Security.Cryptography.ProtectedData> klas lub. <xref:System.Security.Cryptography.ProtectedMemory>  
  
 Poniższa tabela zawiera podsumowanie zadań kryptograficznych w tym temacie.  
  
|Zadanie|Opis|  
|----------|-----------------|  
|Tworzenie aplikacji Windows Forms|Wyświetla listę kontrolek, które są wymagane do uruchomienia aplikacji.|  
|Deklarowanie obiektów globalnych|Deklaruje zmienne ścieżki ciągów, <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> i i ma kontekst <xref:System.Windows.Forms.Form> globalny klasy.|  
|Tworzenie klucza asymetrycznego|Tworzy asymetryczną parę wartości klucza publicznego i prywatnego i przypisuje mu nazwę kontenera kluczy.|  
|Szyfrowanie pliku|Wyświetla okno dialogowe, w którym można wybrać plik do szyfrowania i szyfruje plik.|  
|Odszyfrowywanie pliku|Wyświetla okno dialogowe, w którym można wybrać zaszyfrowany plik do odszyfrowania i odszyfrować plik.|  
|Pobieranie klucza prywatnego|Pobiera pełną parę kluczy przy użyciu nazwy kontenera kluczy.|  
|Eksportowanie klucza publicznego|Zapisuje klucz do pliku XML tylko z parametrami publicznymi.|  
|Importowanie klucza publicznego|Ładuje klucz z pliku XML do kontenera kluczy.|  
|Testowanie aplikacji|Wyświetla listę procedur testowania tej aplikacji.|  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
- Odwołania do <xref:System.IO> przestrzeni nazw <xref:System.Security.Cryptography> i.  
  
## <a name="creating-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 Większość przykładów kodu w tym instruktażu została zaprojektowana jako programy obsługi zdarzeń dla kontrolek Button. Poniższa tabela zawiera listę formantów wymaganych dla przykładowej aplikacji i ich wymaganych nazw w celu dopasowania do przykładów kodu.  
  
|formant|Nazwa|Właściwość Text (zgodnie z wymaganiami)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Szyfruj plik|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Odszyfruj plik|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Utwórz klucze|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Eksportuj klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importuj klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Pobierz klucz prywatny|  
|<xref:System.Windows.Forms.Label>|`label1`|Nie ustawiono klucza|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Kliknij dwukrotnie przyciski w projektancie programu Visual Studio, aby utworzyć obsługę zdarzeń.  
  
## <a name="declaring-global-objects"></a>Deklarowanie obiektów globalnych  
 Dodaj następujący kod do konstruktora formularza. Edytuj zmienne ciągów dla środowiska i preferencji.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Tworzenie klucza asymetrycznego  
 To zadanie tworzy klucz asymetryczny, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucz. Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera kluczy w kontrolce etykieta.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Create Keys` dla przycisku (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Szyfrowanie pliku  
 To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisku (`buttonEncryptFile_Click`) i `EncryptFile` metody. Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.  
  
 Zaszyfrowana zawartość, klucz i IV są zapisywane na jednym <xref:System.IO.FileStream>, który jest nazywany Pakietem szyfrowania.  
  
 `EncryptFile` Metoda wykonuje następujące czynności:  
  
1. Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny do szyfrowania zawartości.  
  
2. Tworzy obiekt służący do <xref:System.Security.Cryptography.RijndaelManaged> szyfrowania klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
3. Używa obiektu do odczytu i <xref:System.IO.FileStream> szyfrowania pliku źródłowego w blokach bajtów do obiektu docelowego <xref:System.IO.FileStream> dla zaszyfrowanego pliku. <xref:System.Security.Cryptography.CryptoStream>  
  
4. Określa długość zaszyfrowanego klucza i IV i tworzy tablicę bajtową wartości ich długości.  
  
5. Zapisuje wartości key, IV i ich długości do zaszyfrowanego pakietu.  
  
 Pakiet szyfrowania używa następującego formatu:  
  
- Długość klucza, bajty 0-3  
  
- Długość IV, bajtów 4-7  
  
- Zaszyfrowany klucz  
  
- IV  
  
- Szyfrowanie tekstu  
  
 Możesz użyć długości klucza i IV, aby określić punkty początkowe i długości wszystkich części pakietu szyfrującego, które mogą być następnie użyte do odszyfrowania pliku.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Encrypt File` dla przycisku (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Dodaj następującą `EncryptFile` metodę do formularza.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Odszyfrowywanie pliku  
 To zadanie obejmuje dwie metody, metodę obsługi zdarzeń dla `Decrypt File` przycisku (`buttonDecryptFile_Click`) i `DecryptFile` metodę. Pierwsza metoda wyświetla okno dialogowe, w którym można wybrać plik i przekazuje jego nazwę pliku do drugiej metody, która wykonuje odszyfrowywanie.  
  
 `Decrypt` Metoda wykonuje następujące czynności:  
  
1. Tworzy algorytm <xref:System.Security.Cryptography.RijndaelManaged> symetryczny służący do odszyfrowywania zawartości.  
  
2. Odczytuje pierwsze osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtów w celu uzyskania długości zaszyfrowanego klucza i IV.  
  
3. Wyodrębnia klucz i IV z pakietu szyfrowania do tablic bajtowych.  
  
4. Tworzy obiekt do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged>klucza. <xref:System.Security.Cryptography.RSACryptoServiceProvider>  
  
5. Używa obiektu do odczytywania i odszyfrowywania sekcji <xref:System.IO.FileStream> szyfrowania tekstu pakietu szyfrowania w blokach bajtów do <xref:System.IO.FileStream> obiektu w odszyfrowanym pliku. <xref:System.Security.Cryptography.CryptoStream> Po zakończeniu odszyfrowywania zostanie zakończone.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Decrypt File` dla przycisku.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Dodaj następującą `DecryptFile` metodę do formularza.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Eksportowanie klucza publicznego  
 To zadanie służy do zapisywania klucza utworzonego przez `Create Keys` przycisk do pliku. Eksportuje tylko parametry publiczne.  
  
 To zadanie symuluje scenariusz dla Alicja przekazującej Roberta swój klucz publiczny, aby mógł szyfrować pliki. Osoby, które mają ten klucz publiczny, nie będą w stanie odszyfrować, ponieważ nie mają pełnej pary kluczy z parametrami prywatnymi.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Export Public Key` dla przycisku (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Importowanie klucza publicznego  
 To zadanie ładuje klucz z tylko parametrami publicznymi, utworzonym przez `Export Public Key` przycisk i ustawia go jako nazwę kontenera kluczy.  
  
 To zadanie symuluje scenariusz ładowania klucza Alicja z tylko parametrami publicznymi, dzięki czemu może zaszyfrować pliki.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Import Public Key` dla przycisku (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Pobieranie klucza prywatnego  
 To zadanie ustawia nazwę kontenera kluczy na nazwę klucza utworzonego za pomocą `Create Keys` przycisku. Kontener kluczy będzie zawierać pełną parę kluczy z parametrami prywatnymi.  
  
 To zadanie symuluje scenariusz Alicja przy użyciu klucza prywatnego w celu odszyfrowania plików zaszyfrowanych przez Robert.  
  
 Dodaj następujący kod jako `Click` procedurę obsługi zdarzeń `Get Private Key` dla przycisku (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Po skompilowaniu aplikacji wykonaj następujące scenariusze testowania.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Aby utworzyć klucze, szyfrowanie i odszyfrowywanie  
  
1. `Create Keys` Kliknij przycisk. Etykieta Wyświetla nazwę klucza i pokazuje, że jest to pełna para kluczy.  
  
2. `Export Public Key` Kliknij przycisk. Należy zauważyć, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.  
  
3. `Encrypt File` Kliknij przycisk i wybierz plik.  
  
4. `Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany.  
  
5. Zapoznaj się z odszyfrowaniem pliku.  
  
6. Zamknij aplikację i uruchom ją ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w następnym scenariuszu.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Aby zaszyfrować przy użyciu klucza publicznego  
  
1. `Import Public Key` Kliknij przycisk. Etykieta Wyświetla nazwę klucza i pokazuje, że jest tylko publiczna.  
  
2. `Encrypt File` Kliknij przycisk i wybierz plik.  
  
3. `Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany. Nie powiedzie się, ponieważ musisz mieć klucz prywatny do odszyfrowania.  
  
 W tym scenariuszu przedstawiono tylko klucz publiczny do szyfrowania pliku dla innej osoby. Zwykle osoba ta może uzyskać tylko klucz publiczny i wstrzymać klucz prywatny do odszyfrowania.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Aby odszyfrować przy użyciu klucza prywatnego  
  
1. `Get Private Key` Kliknij przycisk. Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pełna para kluczy.  
  
2. `Decrypt File` Kliknij przycisk i wybierz plik, który został zaszyfrowany. Ta operacja zakończy się pomyślnie, ponieważ masz pełną parę kluczy do odszyfrowania.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)

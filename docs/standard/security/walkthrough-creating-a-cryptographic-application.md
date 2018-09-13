---
title: 'Wskazówki: tworzenie aplikacji kryptograficznej'
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
ms.openlocfilehash: 873b6120929c8c7cf67d53d8f793964361ae88b8
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708696"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Wskazówki: tworzenie aplikacji kryptograficznej
W tym instruktażu pokazano, jak szyfrowanie i odszyfrowywanie zawartości. Przykłady kodu są przeznaczone dla aplikacji Windows Forms. Ta aplikacja nie przedstawiono tu scenariusze ze świata rzeczywistego, takich jak za pomocą kart inteligentnych. Zamiast tego przedstawiono podstawowe informacje dotyczące szyfrowania i odszyfrowywania.  
  
 W tym instruktażu wykorzystano poniższe wskazówki dotyczące szyfrowania:  
  
-   Użyj <xref:System.Security.Cryptography.RijndaelManaged> klasy algorytm symetryczny, do szyfrowania i odszyfrowywania danych za pomocą jego automatycznie generowanych <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> i <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Użyj <xref:System.Security.Cryptography.RSACryptoServiceProvider>, algorytmu asymetrycznego, do szyfrowania i odszyfrowywania klawisz, aby dane zaszyfrowane przy <xref:System.Security.Cryptography.RijndaelManaged>. Asymetryczne algorytmy najlepiej sprawdzają się dla mniejszych ilości danych, takich jak klucz.  
  
    > [!NOTE]
    >  Aby chronić dane na komputerze, zamiast wymieniać zaszyfrowaną zawartość innym osobom, należy rozważyć użycie <xref:System.Security.Cryptography.ProtectedData> lub <xref:System.Security.Cryptography.ProtectedMemory> klasy.  
  
 Poniższa tabela zawiera podsumowanie zadania kryptograficzne w tym temacie.  
  
|Zadanie|Opis|  
|----------|-----------------|  
|Tworzenie aplikacji Windows Forms|Wyświetla listę formantów, które są wymagane do uruchomienia aplikacji.|  
|Deklarowanie obiektów globalnych|Deklaruje ciągu zmiennych ścieżek <xref:System.Security.Cryptography.CspParameters>i <xref:System.Security.Cryptography.RSACryptoServiceProvider> mają globalne kontekstu <xref:System.Windows.Forms.Form> klasy.|  
|Tworzenie klucza asymetrycznego|Tworzy asymetrycznego publicznych i prywatnych parę klucz-wartość i przypisuje mu nazwę kontenera kluczy.|  
|Szyfrowanie pliku|Wyświetlane jest okno dialogowe, aby wybrać plik do szyfrowania i szyfruje pliku.|  
|Odszyfrowywanie pliku|Wyświetlane jest okno dialogowe, aby wybrać plik zaszyfrowany do odszyfrowywania i odszyfrowuje pliku.|  
|Pobieranie klucza prywatnego|Pobiera pary kluczy pełną nazwę kontenera kluczy.|  
|Eksportowanie klucza publicznego|Zapisuje klucz w pliku XML przy użyciu tylko publiczne parametrów.|  
|Importowanie klucza publicznego|Ładuje klucz z pliku XML do kontenera kluczy.|  
|Testowanie aplikacji|Zawiera listę procedur do testowania tej aplikacji.|  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Odwołuje się do <xref:System.IO> i <xref:System.Security.Cryptography> przestrzeni nazw.  
  
## <a name="creating-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 Większość przykładów kodu w tym przewodniku są przeznaczone do można programy obsługi zdarzeń dla przycisku kontrolki. W poniższej tabeli wymieniono kontrole wymagane dla przykładowej aplikacji i ich wymagane nazwy zgodne z przykładami kodu.  
  
|Formant|Nazwa|Właściwość Text (zgodnie z potrzebami)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Szyfrowanie pliku|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Odszyfrowywanie pliku|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Tworzenie kluczy|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Wyeksportuj klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importuj klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Pobierz klucz prywatny|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Kliknij dwukrotnie przycisków w Projektancie Visual Studio do tworzenia swoich programów obsługi zdarzeń.  
  
## <a name="declaring-global-objects"></a>Deklarowanie obiektów globalnych  
 Dodaj następujący kod do formularza konstruktora. Edytowanie zmiennych ciągu dla Twojego środowiska i swoich preferencji.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Tworzenie klucza asymetrycznego  
 To zadanie tworzy klucza asymetrycznego, któremu szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucza. Ten klucz został użyty do zaszyfrowania zawartości, i wyświetla nazwę kontenera kluczy na formant etykiety.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Create Keys` przycisku (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Szyfrowanie pliku  
 To zadanie polega na dwa sposoby: metoda obsługi zdarzeń dla `Encrypt File` przycisku (`buttonEncryptFile_Click`) i `EncryptFile` metody. Pierwsza metoda wyświetlane jest okno dialogowe wybierania plik i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.  
  
 Zaszyfrowaną zawartość, klucza i IV są zapisywane do jednego <xref:System.IO.FileStream>, który jest nazywany pakietu szyfrowania.  
  
 `EncryptFile` Metoda wykonuje następujące czynności:  
  
1.  Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytm symetryczny zawartość.  
  
2.  Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do zaszyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.  
  
3.  Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i szyfrowania <xref:System.IO.FileStream> pliku źródłowego w blokach bajtów do miejsca docelowego <xref:System.IO.FileStream> obiektu dla zaszyfrowanego pliku.  
  
4.  Określa długość zaszyfrowanego klucza i IV i tworzy tablice typu byte ich wartości długości.  
  
5.  Zapisuje klucz, IV i ich wartości długości zaszyfrowany pakiet.  
  
 Pakietu szyfrowania posługuje się następującym formatem:  
  
-   Długość klucza, bajty 0 – 3  
  
-   Długość IV, w bajtach 4 – 7  
  
-   Zaszyfrowany klucz  
  
-   IV  
  
-   Zaszyfrowanego tekstu  
  
 Długości klucza i IV służy do określenia punktów początkowej i długości wszystkich części pakietu szyfrowania, które następnie mogą być używane do odszyfrowywania pliku.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Encrypt File` przycisku (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Dodaj następujący kod `EncryptFile` metody do formularza.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Odszyfrowywanie pliku  
 To zadanie obejmuje dwie metody, metody obsługi zdarzeń dla `Decrypt File` przycisku (`buttonDecryptFile_Click`), a `DecryptFile` metody. Pierwsza metoda wyświetlane jest okno dialogowe wybierania plik i przekazuje jego nazwa pliku do drugiej metody, która wykonuje odszyfrowywania.  
  
 `Decrypt` Metoda wykonuje następujące czynności:  
  
1.  Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytm symetryczny do odszyfrowania zawartości.  
  
2.  Odczytuje pierwsze 8 bajtów z <xref:System.IO.FileStream> pakietu zaszyfrowane w tablice bajtów w celu uzyskania długości zaszyfrowanego klucza i IV.  
  
3.  Wyodrębnia klucz i IV z pakietu szyfrowania do tablice typu byte.  
  
4.  Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.  
  
5.  Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i odszyfrować części tekstowej szyfrowania <xref:System.IO.FileStream> szyfrowanie pakietów, w blokach bajtów w <xref:System.IO.FileStream> obiekt odszyfrowanego pliku. Po jej zakończeniu odszyfrowywania został ukończony.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Decrypt File` przycisku.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Dodaj następujący kod `DecryptFile` metody do formularza.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Eksportowanie klucza publicznego  
 To zadanie powoduje zapisanie klucza utworzonego na podstawie `Create Keys` przycisku do pliku. Eksportuje ona tylko publiczne parametrów.  
  
 To zadanie symuluje scenariusza Alicja, zapewniając Bob jej klucz publiczny, tak, aby on szyfrowania plików dla jej. ADAM i innym osobom mający ten klucz nie będzie ich odszyfrować, ponieważ nie mają pary pełnej kluczy prywatnych parametrami.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Export Public Key` przycisku (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Importowanie klucza publicznego  
 To zadanie ładowania klucza z parametrami tylko publiczne tworzony przez `Export Public Key` znajdujący się i ustawia go jako nazwę kontenera kluczy.  
  
 To zadanie symuluje scenariusza Bob ładowania klucza Alicji parametrami tylko publiczne, więc on szyfrowania plików dla jej.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Import Public Key` przycisku (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Pobieranie klucza prywatnego  
 To zadanie ustawia nazwę kontenera kluczy, nazwę klucza utworzonego za pomocą `Create Keys` przycisku. Kontener kluczy będzie zawierać pary pełnej kluczy prywatnych parametrami.  
  
 To zadanie symuluje scenariusza Alicji przy użyciu swojego klucza prywatnego do odszyfrowania zaszyfrowanych przez Boba plików.  
  
 Dodaj następujący kod jako `Click` program obsługi zdarzeń dla `Get Private Key` przycisku (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Po skonstruowaniu aplikacji, należy wykonać następujące scenariusze testowania.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Aby utworzyć klucze, szyfrowania i odszyfrowywania  
  
1.  Kliknij przycisk `Create Keys` przycisku. Etykieta Wyświetla nazwę klucza i wskazuje, że jest parą kluczy pełnej.  
  
2.  Kliknij przycisk `Export Public Key` przycisku. Należy pamiętać, że eksportowanie parametrów klucza publicznego nie zmienia bieżącego klucza.  
  
3.  Kliknij przycisk `Encrypt File` przycisku i wybierz plik.  
  
4.  Kliknij przycisk `Decrypt File` i wybierz plik, po prostu szyfrowane.  
  
5.  Zapoznaj się z plikiem, po prostu odszyfrować.  
  
6.  Zamknij aplikację i uruchom ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w kolejnym scenariuszu.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Aby zaszyfrować przy użyciu klucza publicznego  
  
1.  Kliknij przycisk `Import Public Key` przycisku. Etykieta Wyświetla nazwę klucza i pokazuje, że nie jest publiczny wyłącznie.  
  
2.  Kliknij przycisk `Encrypt File` przycisku i wybierz plik.  
  
3.  Kliknij przycisk `Decrypt File` i wybierz plik, po prostu szyfrowane. To zakończy się niepowodzeniem, ponieważ konieczne jest posiadanie klucza prywatnego do odszyfrowania.  
  
 Ten scenariusz pokazuje, posiadające klucza publicznego do szyfrowania plików dla innej osoby. Zazwyczaj tej osobie umożliwiają tylko klucz publiczny i wstrzymania klucza prywatnego do odszyfrowania.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Aby odszyfrować, używając klucza prywatnego  
  
1.  Kliknij przycisk `Get Private Key` przycisku. Etykieta Wyświetla nazwę klucza i pokazuje, czy jest to pary kluczy pełnej.  
  
2.  Kliknij przycisk `Decrypt File` i wybierz plik, po prostu szyfrowane. To powiedzie się, ponieważ masz pary pełnej kluczy do odszyfrowania.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)

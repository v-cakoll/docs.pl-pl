---
title: "Wskazówki: tworzenie aplikacji kryptograficznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869d35a15a028e6df09dea281ac653ab8b9a28d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Wskazówki: tworzenie aplikacji kryptograficznej
W tym przewodniku pokazano, jak do szyfrowania i odszyfrowywania zawartości. Przykłady kodu są przeznaczone dla aplikacji formularzy systemu Windows. Ta aplikacja nie wykazują rzeczywistych scenariuszach, takich jak za pomocą kart inteligentnych. Zamiast tego należy go przedstawiono podstawowe informacje dotyczące szyfrowania i odszyfrowywania.  
  
 W tym przewodniku zastosowano następujące wytyczne szyfrowania:  
  
-   Użyj <xref:System.Security.Cryptography.RijndaelManaged> klasy algorytmu symetrycznego, do szyfrowania i odszyfrowywania danych przy użyciu jego automatycznie generowanych <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> i <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Użyj <xref:System.Security.Cryptography.RSACryptoServiceProvider>, algorytmu asymetrycznego, do szyfrowania i odszyfrowywania klucza do danych zaszyfrowanych przez <xref:System.Security.Cryptography.RijndaelManaged>. Asymetryczne algorytmy najlepiej są używane w przypadku mniejszych ilości danych, takich jak klucza.  
  
    > [!NOTE]
    >  Aby chronić dane na komputerze zamiast wymiany zaszyfrowaną zawartość z innych osób, należy rozważyć użycie <xref:System.Security.Cryptography.ProtectedData> lub <xref:System.Security.Cryptography.ProtectedMemory> klasy.  
  
 W poniższej tabeli przedstawiono zadania kryptograficzne, w tym temacie.  
  
|Zadanie|Opis|  
|----------|-----------------|  
|Tworzenie aplikacji formularzy systemu Windows|Zawiera listę funkcji, które są wymagane do uruchomienia aplikacji.|  
|Deklarowanie obiektów globalnych|Deklaruje zmienne ścieżek w ciągu <xref:System.Security.Cryptography.CspParameters>i <xref:System.Security.Cryptography.RSACryptoServiceProvider> ma globalne kontekście <xref:System.Windows.Forms.Form> klasy.|  
|Tworzenie klucza asymetrycznego|Tworzy asymetrycznego publiczne i prywatne para klucz-wartość i przypisuje mu nazwę kontenera kluczy.|  
|System szyfrowania plików|Wyświetla okno dialogowe, aby wybrać plik do szyfrowania i szyfruje plik.|  
|Odszyfrowywanie pliku|Wyświetla okno dialogowe, aby wybrać zaszyfrowanego pliku do odszyfrowywania i odszyfrowuje pliku.|  
|Wprowadzenie klucza prywatnego.|Pobiera pary pełnej kluczy przy użyciu nazwy kontenera kluczy.|  
|Eksportowanie klucza publicznego|Klucz jest zapisywany do pliku XML z tylko publiczne parametrów.|  
|Importowanie klucza publicznego|Ładuje klucz z pliku XML do kontenera kluczy.|  
|Testowanie aplikacji|Zawiera listę procedur do testowania tej aplikacji.|  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Odwołuje się do <xref:System.IO> i <xref:System.Security.Cryptography> przestrzeni nazw.  
  
## <a name="creating-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 Większość przykładów kodu, w tym przewodniku są zaprojektowane jako programy obsługi zdarzeń dla kontrolek przycisku. W poniższej tabeli wymieniono formantów, wymaganych do przykładowej aplikacji i ich nazw wymagane zgodne z przykładami kodu.  
  
|Formant|Nazwa|Właściwość Text (w razie potrzeby)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Szyfrowanie plików|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Odszyfrowywania plików|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Tworzenie kluczy|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Wyeksportować klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importuj klucz publiczny|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Pobierz klucz prywatny|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Kliknij dwukrotnie przycisków w projektancie programu Visual Studio do tworzenia swoich programów obsługi zdarzeń.  
  
## <a name="declaring-global-objects"></a>Deklarowanie obiektów globalnych  
 Dodaj następujący kod do konstruktora formularza. Edytowanie zmiennych ciągu dla Twojego środowiska i swoich preferencji.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Tworzenie klucza asymetrycznego  
 To zadanie tworzy klucza asymetrycznego, który szyfruje i odszyfrowuje <xref:System.Security.Cryptography.RijndaelManaged> klucza. Ten klucz został użyty do zaszyfrowania zawartości i wyświetla nazwę kontenera klucza na formantu etykiety.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Create Keys` przycisk (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>System szyfrowania plików  
 To zadanie obejmuje dwie metody: metoda obsługi zdarzeń dla `Encrypt File` przycisk (`buttonEncryptFile_Click`) i `EncryptFile` metody. Pierwsza metoda Wyświetla okno dialogowe wybierania pliku i przekazuje nazwę pliku do drugiej metody, która wykonuje szyfrowanie.  
  
 Zaszyfrowaną zawartość, klucz i IV są zapisywane do jednego <xref:System.IO.FileStream>, który jest określany jako pakietu szyfrowania.  
  
 `EncryptFile` Metoda wykonuje następujące czynności:  
  
1.  Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytmu symetrycznego zawartość.  
  
2.  Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do szyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.  
  
3.  Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i szyfrowania <xref:System.IO.FileStream> pliku źródłowego w blokach bajtów do miejsca docelowego <xref:System.IO.FileStream> obiektu dla zaszyfrowany plik.  
  
4.  Określa długość zaszyfrowanego klucza i IV i tworzy tablice typu byte ich wartości długości.  
  
5.  Zapisuje klucz, IV i ich wartości długości zaszyfrowanego pakietu.  
  
 Pakietu szyfrowania używany następujący format:  
  
-   Długość klucza bajtów 0 - 3  
  
-   Długość IV, bajtów 4-7  
  
-   Zaszyfrowany klucz  
  
-   IV  
  
-   Tekst zaszyfrowany  
  
 Długość klucza i IV służy do określenia punkty początkowy i długości wszystkie części pakietu szyfrowania, które mogą być następnie używane do odszyfrowywania pliku.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Encrypt File` przycisk (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Dodaj następujące `EncryptFile` metody do formularza.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Odszyfrowywanie pliku  
 To zadanie obejmuje dwie metody, metoda obsługi zdarzeń dla `Decrypt File` przycisk (`buttonEncryptFile_Click`) i `DecryptFile` metody. Pierwsza metoda Wyświetla okno dialogowe wybierania pliku i przekazuje jego nazwa pliku do drugiej metody, która wykonuje odszyfrowywanie.  
  
 `Decrypt` Metoda wykonuje następujące czynności:  
  
1.  Tworzy <xref:System.Security.Cryptography.RijndaelManaged> algorytmu symetrycznego do odszyfrowywania zawartości.  
  
2.  Odczytuje pierwszych osiem bajtów <xref:System.IO.FileStream> zaszyfrowanego pakietu do tablic bajtowych można uzyskać długości zaszyfrowanego klucza i IV.  
  
3.  Pobiera klucz i IV z pakietu szyfrowania na tablice typu byte.  
  
4.  Tworzy <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do odszyfrowania <xref:System.Security.Cryptography.RijndaelManaged> klucza.  
  
5.  Używa <xref:System.Security.Cryptography.CryptoStream> obiektu do odczytu i do odszyfrowywania sekcji tekstu szyfrowania <xref:System.IO.FileStream> szyfrowania pakietów, w blokach bajtów w <xref:System.IO.FileStream> obiektu odszyfrowane pliku. Po jej zakończeniu, odszyfrowywanie zostało ukończone.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Decrypt File` przycisku.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Dodaj następujące `DecryptFile` metody do formularza.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Eksportowanie klucza publicznego  
 To zadanie jest zapisywany klucza utworzonego na podstawie `Create Keys` przycisku do pliku. Eksportuje go tylko publiczne parametrów.  
  
 To zadanie symuluje scenariusza Alicja nadanie Bob jej klucz publiczny, aby on szyfrowania plików dla jej. On i innych użytkowników mających tego klucza publicznego nie będą stanie ich odszyfrować, ponieważ nie mają pary pełnej kluczy prywatnych parametrów.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Export Public Key` przycisk (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Importowanie klucza publicznego  
 To zadanie ładuje klucza z parametrami tylko publiczne, tworzony przez `Export Public Key` przycisk i ustawia go jako nazwa kontenera kluczy.  
  
 To zadanie symuluje scenariusza Bob ładowania klucza Alicji parametrami tylko publiczne, więc on szyfrowania plików dla jej.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Import Public Key` przycisk (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Wprowadzenie klucza prywatnego  
 To zadanie umożliwia ustawienie nazwy kontenera kluczy nazwę klucza utworzone za pomocą `Create Keys` przycisku. Kontener kluczy będzie zawierać pary pełnej kluczy prywatnych parametrów.  
  
 To zadanie symuluje scenariusza Alicji przy użyciu swojego klucza prywatnego do odszyfrowywania plików zaszyfrowanych przez niego.  
  
 Dodaj następujący kod jako `Click` programu obsługi zdarzeń dla `Get Private Key` przycisk (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Po skonstruowaniu aplikacji, należy wykonać następujące scenariusze testowania.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Do tworzenia kluczy, szyfrowania i odszyfrowywania  
  
1.  Kliknij przycisk `Create Keys` przycisku. Etykieta Wyświetla nazwę klucza i wskazuje, że jest pary kluczy pełnej.  
  
2.  Kliknij przycisk `Export Public Key` przycisku. Należy pamiętać, że eksportowanie parametrów klucza publicznego nie zmienia się bieżący klucz.  
  
3.  Kliknij przycisk `Encrypt File` i wybrać plik.  
  
4.  Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane.  
  
5.  Zapoznaj się z plikiem tylko odszyfrować.  
  
6.  Zamknij aplikację i uruchom ponownie, aby przetestować pobieranie utrwalonych kontenerów kluczy w scenariuszu dalej.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Do szyfrowania za pomocą klucza publicznego  
  
1.  Kliknij przycisk `Import Public Key` przycisku. Etykieta Wyświetla nazwę klucza i wskazuje, że jest publiczny wyłącznie.  
  
2.  Kliknij przycisk `Encrypt File` i wybrać plik.  
  
3.  Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane. To zakończy się niepowodzeniem, ponieważ musi mieć klucz prywatny do odszyfrowania.  
  
 W tym scenariuszu pokazano, po klucz publiczny do zaszyfrowania pliku innej osoby. Zwykle ta osoba umożliwiają tylko klucz publiczny i wstrzymania klucza prywatnego do odszyfrowania.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Można odszyfrować za pomocą klucza prywatnego  
  
1.  Kliknij przycisk `Get Private Key` przycisku. Etykieta Wyświetla nazwę klucza i wskazuje, czy jest pary kluczy pełnej.  
  
2.  Kliknij przycisk `Decrypt File` i wybrać plik tylko zaszyfrowane. Są to powiodło się ponieważ pary kluczy pełnej do odszyfrowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)

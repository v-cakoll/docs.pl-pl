---
title: 'Instrukcje: Odczytaj metadane obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: a22085e0bbaeda1a166c6d46b2604858fb403d8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741447"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="31a3b-102">Instrukcje: Odczytaj metadane obrazu</span><span class="sxs-lookup"><span data-stu-id="31a3b-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="31a3b-103">Niektóre pliki obrazu zawierają metadane, które mogą odczytać w celu określenia funkcji obrazu.</span><span class="sxs-lookup"><span data-stu-id="31a3b-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="31a3b-104">Na przykład cyfrowych fotografii może zawierać metadane, które mogą odczytać w celu określenia producenta i modelu aparatu używane do przechwytywania obrazu.</span><span class="sxs-lookup"><span data-stu-id="31a3b-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="31a3b-105">Za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], mogą odczytywać metadane istniejącego i można także zapisać nowe metadane do plików obrazu.</span><span class="sxs-lookup"><span data-stu-id="31a3b-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="31a3b-106">przechowuje wyraźne metadanych w <xref:System.Drawing.Imaging.PropertyItem> obiektu.</span><span class="sxs-lookup"><span data-stu-id="31a3b-106">stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="31a3b-107">Może odczytywać <xref:System.Drawing.Image.PropertyItems%2A> właściwość <xref:System.Drawing.Image> obiekt, aby pobrać wszystkie metadane z pliku.</span><span class="sxs-lookup"><span data-stu-id="31a3b-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="31a3b-108"><xref:System.Drawing.Image.PropertyItems%2A> Właściwość zwraca tablicę <xref:System.Drawing.Imaging.PropertyItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="31a3b-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="31a3b-109">A <xref:System.Drawing.Imaging.PropertyItem> obiekt ma następujące cztery właściwości: `Id`, `Value`, `Len`, i `Type`.</span><span class="sxs-lookup"><span data-stu-id="31a3b-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="31a3b-110">Id</span><span class="sxs-lookup"><span data-stu-id="31a3b-110">Id</span></span>  
 <span data-ttu-id="31a3b-111">Tag, który identyfikuje element metadanych.</span><span class="sxs-lookup"><span data-stu-id="31a3b-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="31a3b-112">Niektóre wartości, które mogą być przypisane do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> przedstawiono w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="31a3b-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="31a3b-113">Wartość szesnastkowa</span><span class="sxs-lookup"><span data-stu-id="31a3b-113">Hexadecimal value</span></span>|<span data-ttu-id="31a3b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="31a3b-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="31a3b-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="31a3b-115">0x0320</span></span><br /><br /> <span data-ttu-id="31a3b-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="31a3b-116">0x010F</span></span><br /><br /> <span data-ttu-id="31a3b-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="31a3b-117">0x0110</span></span><br /><br /> <span data-ttu-id="31a3b-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="31a3b-118">0x9003</span></span><br /><br /> <span data-ttu-id="31a3b-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="31a3b-119">0x829A</span></span><br /><br /> <span data-ttu-id="31a3b-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="31a3b-120">0x5090</span></span><br /><br /> <span data-ttu-id="31a3b-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="31a3b-121">0x5091</span></span>|<span data-ttu-id="31a3b-122">Tytuł obrazu</span><span class="sxs-lookup"><span data-stu-id="31a3b-122">Image title</span></span><br /><br /> <span data-ttu-id="31a3b-123">Producent sprzętu</span><span class="sxs-lookup"><span data-stu-id="31a3b-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="31a3b-124">Model urządzenia</span><span class="sxs-lookup"><span data-stu-id="31a3b-124">Equipment model</span></span><br /><br /> <span data-ttu-id="31a3b-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="31a3b-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="31a3b-126">Czas narażenia EXIF</span><span class="sxs-lookup"><span data-stu-id="31a3b-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="31a3b-127">Tabela jasności</span><span class="sxs-lookup"><span data-stu-id="31a3b-127">Luminance table</span></span><br /><br /> <span data-ttu-id="31a3b-128">Tabela Chrominance</span><span class="sxs-lookup"><span data-stu-id="31a3b-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="31a3b-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="31a3b-129">Value</span></span>  
 <span data-ttu-id="31a3b-130">Tablica wartości.</span><span class="sxs-lookup"><span data-stu-id="31a3b-130">An array of values.</span></span> <span data-ttu-id="31a3b-131">Format wartości jest określany przez <xref:System.Drawing.Imaging.PropertyItem.Type%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="31a3b-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="31a3b-132">Len</span><span class="sxs-lookup"><span data-stu-id="31a3b-132">Len</span></span>  
 <span data-ttu-id="31a3b-133">Długość (w bajtach) tablica wartości wskazywany przez <xref:System.Drawing.Imaging.PropertyItem.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="31a3b-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="31a3b-134">Typ</span><span class="sxs-lookup"><span data-stu-id="31a3b-134">Type</span></span>  
 <span data-ttu-id="31a3b-135">Typ danych wartości w tablicy, wskazywana przez `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="31a3b-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="31a3b-136">Formaty wskazywanym przez `Type` w poniższej tabeli przedstawiono wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="31a3b-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="31a3b-137">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="31a3b-137">Numeric value</span></span>|<span data-ttu-id="31a3b-138">Opis</span><span class="sxs-lookup"><span data-stu-id="31a3b-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="31a3b-139">1</span><span class="sxs-lookup"><span data-stu-id="31a3b-139">1</span></span>|<span data-ttu-id="31a3b-140">A `Byte`</span><span class="sxs-lookup"><span data-stu-id="31a3b-140">A `Byte`</span></span>|  
|<span data-ttu-id="31a3b-141">2</span><span class="sxs-lookup"><span data-stu-id="31a3b-141">2</span></span>|<span data-ttu-id="31a3b-142">Tablica `Byte` obiektów zakodowanymi w formacie ASCII</span><span class="sxs-lookup"><span data-stu-id="31a3b-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="31a3b-143">3</span><span class="sxs-lookup"><span data-stu-id="31a3b-143">3</span></span>|<span data-ttu-id="31a3b-144">16-bitową liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="31a3b-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="31a3b-145">4</span><span class="sxs-lookup"><span data-stu-id="31a3b-145">4</span></span>|<span data-ttu-id="31a3b-146">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="31a3b-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="31a3b-147">5</span><span class="sxs-lookup"><span data-stu-id="31a3b-147">5</span></span>|<span data-ttu-id="31a3b-148">Tablica dwóch `Byte` obiekty reprezentujące Liczba wymierna</span><span class="sxs-lookup"><span data-stu-id="31a3b-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="31a3b-149">6</span><span class="sxs-lookup"><span data-stu-id="31a3b-149">6</span></span>|<span data-ttu-id="31a3b-150">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="31a3b-150">Not used</span></span>|  
|<span data-ttu-id="31a3b-151">7</span><span class="sxs-lookup"><span data-stu-id="31a3b-151">7</span></span>|<span data-ttu-id="31a3b-152">Niezdefiniowane</span><span class="sxs-lookup"><span data-stu-id="31a3b-152">Undefined</span></span>|  
|<span data-ttu-id="31a3b-153">8</span><span class="sxs-lookup"><span data-stu-id="31a3b-153">8</span></span>|<span data-ttu-id="31a3b-154">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="31a3b-154">Not used</span></span>|  
|<span data-ttu-id="31a3b-155">9</span><span class="sxs-lookup"><span data-stu-id="31a3b-155">9</span></span>|`SLong`|  
|<span data-ttu-id="31a3b-156">10</span><span class="sxs-lookup"><span data-stu-id="31a3b-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="31a3b-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="31a3b-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="31a3b-158">Opis</span><span class="sxs-lookup"><span data-stu-id="31a3b-158">Description</span></span>  
 <span data-ttu-id="31a3b-159">Poniższy przykład kodu odczytuje i wyświetla siedem elementów metadanych w pliku `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="31a3b-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="31a3b-160">Drugi element właściwości (indeks 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (zakodowany w formacie ASCII byte array).</span><span class="sxs-lookup"><span data-stu-id="31a3b-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="31a3b-161">Przykład kodu wyświetla wartość tego elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="31a3b-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="31a3b-162">Kod generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="31a3b-162">The code produces output similar to the following:</span></span>  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a><span data-ttu-id="31a3b-163">Kod</span><span class="sxs-lookup"><span data-stu-id="31a3b-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="31a3b-164">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="31a3b-164">Compiling the Code</span></span>  
 <span data-ttu-id="31a3b-165">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="31a3b-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="31a3b-166">Obsługa formularzy <xref:System.Windows.Forms.Control.Paint> zdarzeń i wklej ten kod do obsługi zdarzeń malowania.</span><span class="sxs-lookup"><span data-stu-id="31a3b-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="31a3b-167">Należy zastąpić `FakePhoto.jpg` przy użyciu nazwy obrazu i ścieżki prawidłowe dla używanego systemu i importowania `System.Drawing.Imaging` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="31a3b-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a3b-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31a3b-168">See also</span></span>
- [<span data-ttu-id="31a3b-169">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="31a3b-169">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="31a3b-170">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="31a3b-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)

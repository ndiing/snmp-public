# Dokumentasi API SNMP

Dokumen ini menyediakan detail dan contoh untuk berinteraksi dengan API SNMP.

---

## Otorisasi

Semua permintaan ke API SNMP memerlukan token otorisasi dalam header `Authorization`:

```http
Authorization: Bearer {{token}}
```

---

## Contoh Format Token

```json
@token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0YXJnZXQiOiIxMDMuMjguMTQ4LjIwMiIsImNvbW11bml0eSI6InByaXZhdGUiLCJ0eXBlIjoienRlL2MzMjB2MiIsIm9wdGlvbnMiOnsicG9ydCI6MTY2MX19.VD9UjI2fM2g3Nt07HtIKpAreLDrIFM5PsWdnNIsKvmo
```

---

## Endpoint API

### `/api/snmp/token`

**Permintaan:**

```http
POST http://localhost/api/snmp/token
Content-Type: application/json

{
    "target": "103.28.148.202",
    "community": "private",
    "type": "zte/c320v2",
    "options": {
        "port": 1661
    }
}
```

---

### `/api/snmp/find/:path`

#### Cari Object MIB berdasarkan OID

**Permintaan:**

```http
GET http://localhost/api/snmp/find/1.3.6.1.4.1.3902.1082.500.20.2.2.2.1.14
Authorization: Bearer {{token}}
```

#### Cari Object MIB berdasarkan NID

**Permintaan:**

```http
GET http://localhost/api/snmp/find/iso.org.dod.internet.private.enterprises.zte.zxAccessNode.zxAnPon.zxAnGponRemoteOnuMib.zxAnGponRmOnuObjects.zxAnGponRmAniObjects.zxAnGponRmAniTable.zxAnGponRmAniEntry.zxAnGponRmAniTxOptLevel
Authorization: Bearer {{token}}
```

#### Cari Object MIB berdasarkan Nama

**Permintaan:**

```http
GET http://localhost/api/snmp/find/zxAnGponRmAniTxOptLevel
Authorization: Bearer {{token}}
```

---

### `/api/snmp/find-closest/:path`

#### Cari Object MIB Terdekat berdasarkan Full OID

**Permintaan:**

```http
GET http://localhost/api/snmp/find-closest/1.3.6.1.4.1.3902.1082.500.20.2.2.2.1.14.285278721.1.1
Authorization: Bearer {{token}}
```

#### Cari Object MIB Terdekat berdasarkan Base OID

**Permintaan:**

```http
GET http://localhost/api/snmp/find-closest/1.3.6.1.4.1.3902.1082.500.20.2.2.2.1.14
Authorization: Bearer {{token}}
```

---

### `/api/snmp/get/:path/:id`

#### Mengambil Nilai dari OID Tertentu

**Permintaan:**

```http
GET http://localhost/api/snmp/get/:path/:id
Authorization: Bearer {{token}}
```

---

### `/api/snmp/get-next/:path`

#### Mengambil Nilai dari OID Berikutnya

**Permintaan:**

```http
GET http://localhost/api/snmp/get-next/:path
Authorization: Bearer {{token}}
```

---

### `/api/snmp/set/:path/:id`

#### Mengatur Nilai dari OID Tertentu

**Permintaan:**

```http
POST http://localhost/api/snmp/set/:path/:id
Authorization: Bearer {{token}}
Content-Type: application/json

{

}
```

---

### `/api/snmp/subtree/:path`

#### Mengambil Semua Data dari Subtree OID

**Permintaan:**

```http
GET http://localhost/api/snmp/subtree/:path
Authorization: Bearer {{token}}
```

---

### `/api/snmp/table/:path`

#### Mengambil Data dari Tabel Terstruktur

**Permintaan:**

```http
GET http://localhost/api/snmp/table/:path
Authorization: Bearer {{token}}
```

---

### `/api/snmp/walk/:path`

#### Menjelajahi OID dan Subtree

**Permintaan:**

```http
GET http://localhost/api/snmp/walk/:path
Authorization: Bearer {{token}}
```

---

### `/api/snmp/:path/:id`

#### Dari `GET`

**Permintaan:**

```http
GET http://localhost/api/snmp/:path/:id
Authorization: Bearer {{token}}
```

#### Dari `POST`

**Permintaan:**

```http
POST http://localhost/api/snmp/:path/:id
Authorization: Bearer {{token}}
Content-Type: application/json

{

}
```

---

### `/api/snmp/:path`

#### Dari Subtree/Tabel

**Permintaan:**

```http
GET http://localhost/api/snmp/:path
Authorization: Bearer {{token}}
```

---

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/ndiing/snmp">dinetkan snmp</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://github.com/ndiing">ndiing</a> is licensed under <a href="https://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""></a></p>
# ⚙️ Solució Activitat T02 - Selecció d’un SAI per una empresa client

## 🧩 Índex
1. [Introducció](#introducció)
2. [Inventari d’equips](#inventari-déquips)
3. [Càlcul de potència total](#càlcul-de-potència-total)
4. [Determinació de l’autonomia](#determinació-de-lautonomia)
5. [Recerca de models de SAI](#recerca-de-models-de-sai)
6. [Recomanació final](#recomanació-final)
7. [Fonts i enllaços](#fonts-i-enllaços)
8. [Imatges i annexos](#imatges-i-annexos)

---

## 🧭 Introducció
L’empresa **TecnoGestió S.L.**, dedicada a la gestió documental i assessorament informàtic, ha experimentat incidències elèctriques recurrents.  
Per garantir la continuïtat del servei i protegir els equips, s’ha realitzat un **estudi tècnic per seleccionar el SAI més adequat** segons les necessitats del despatx.

L’estudi inclou:
- Inventari d’equips crítics.  
- Càlcul de consum total i potència necessària.  
- Estimació d’autonomia requerida.  
- Comparativa de models de SAI i justificació de la selecció final.

---

## 🖥️ Inventari d’equips

| Dispositiu | Quantitat | Model i referència | Consum (W) | Consum (VA) | Comentaris |
|-------------|------------|--------------------|-------------|--------------|-------------|
| Ordinador de sobretaula | 4 | [PcCom Work Intel Core i5-12400 / 32GB / 2TB SSD + Windows 11 Pro](https://www.pccomponentes.com/ordenador-sobremesa-pccom-work-intel-core-i5-12400-32gb-2tb-ssd-windows-11-pro) | 500 | 625 | Essencials per mantenir la feina i evitar pèrdua de dades. |
| Monitor 27" | 4 | [Alurin CoreVision 27" IPS 4K](https://www.pccomponentes.com/monitor-alurin-corevision-27-ips-4k-freesync-altura-regulable?refurbished) | 48 | 60 | Necessaris per interactuar amb els equips durant el tall. |
| Router | 1 | [TP-Link Archer AX53](https://www.tp-link.com/es/home-networking/wifi-router/archer-ax53/#specifications) | 12 | 15 | Permet connexió i transferència de dades al núvol. |
| Impressora multifunció | 1 | [HP LaserJet Pro MFP M428fdw](https://pcb.inc.hp.com/dc/api/spec-sheet/ww-en/19204100/pdf/W1A30A.pdf) | 510 | 637 | No es connectarà al SAI pel seu alt consum i poca criticitat. |

**Total consum connectat:**  
`(500 x 4) + (48 x 4) + 12 = 2204 W`

---

## ⚡ Càlcul de potència total

El factor de potència estimat és **0,7**, per tant:

> 2204 W ÷ 0,7 = **3149 VA**

Per seguretat, s’aplica un marge del 20% addicional:

> 3149 VA × 1,20 = **3779 VA**

**Potència recomanada del SAI:** entre **3000 i 4000 VA**

---

## 🔋 Determinació de l’autonomia
S’estima que una **autonomia entre 10 i 20 minuts** és suficient per:
- Desar documents oberts.
- Finalitzar tasques actives.
- Apagar correctament tots els equips.

Es recomana un model amb **mínim 15 minuts d’autonomia** per garantir marge davant càrregues imprevistes.

---

## 🔍 Recerca de models de SAI

| Model | Potència (VA/W) | Autonomia | Tipus | Característiques destacades | Enllaç |
|--------|------------------|------------|--------|------------------------------|--------|
| **Phasak Protekt PH 7631** | 3160 VA / 2100 W | 10-15 min | Line-interactive | Ona sinusoidal pura, AVR, pantalla LCD, connexió RS-232/USB | [PCComponentes](https://www.pccomponentes.com/phasak-protekt-ph-7631-3160va-sai-rack) |
| **Salicru SLC Twin RT2** | 3000 VA / 2700 W | 12-20 min | On-line doble conversió | Màxima estabilitat, protecció avançada, format rack 2U | [PCComponentes](https://www.pccomponentes.com/salicru-slc-twin-rt2-sai-on-line-3000-va) |

---

## 🧾 Recomanació final

### ✅ Model recomanat: **Phasak Protekt PH 7631 – 3160VA SAI Rack**

**Motivació tècnica:**
- **Potència suficient (3160 VA / 2100 W)** per cobrir el consum total (3779 VA amb reserva).
- **Autonomia de 10-15 minuts**, ajustada a les necessitats del client.
- **Ona sinusoidal pura** i **AVR** (regulació automàtica de voltatge), ideals per protegir equips informàtics sensibles.
- **Format Rack 2U**, que optimitza l’espai i facilita la instal·lació professional.
- **Preu competitiu** dins del segment empresarial.

---

## 📚 Fonts i enllaços
- [PcCom Work Intel Core i5-12400 / 32GB / 2TB SSD + Windows 11 Pro](https://www.pccomponentes.com/ordenador-sobremesa-pccom-work-intel-core-i5-12400-32gb-2tb-ssd-windows-11-pro)  
- [Alurin CoreVision 27" IPS 4K](https://www.pccomponentes.com/monitor-alurin-corevision-27-ips-4k-freesync-altura-regulable?refurbished)  
- [HP LaserJet Pro MFP M428fdw](https://pcb.inc.hp.com/dc/api/spec-sheet/ww-en/19204100/pdf/W1A30A.pdf)  
- [TP-Link Archer AX53](https://www.tp-link.com/es/home-networking/wifi-router/archer-ax53/#specifications)  
- [Phasak Protekt PH 7631](https://www.pccomponentes.com/phasak-protekt-ph-7631-3160va-sai-rack)  
- [Salicru SLC Twin RT2](https://www.pccomponentes.com/salicru-slc-twin-rt2-sai-on-line-3000-va)

---

## 🖼️ Imatges i annexos
| Imatge | Descripció |
|:-------|:------------|
| ![Esquema de connexió del SAI](./img/esquema_SAI.png "Connexió dels equips a través del SAI") | Distribució dels equips connectats |
| ![Comparativa de models](./img/comparativa_models.png "Comparativa de característiques dels models analitzats") | Taula de comparació entre Phasak i Salicru |

---

**Conclusió:**  
El model **Phasak Protekt PH 7631** és l’opció més equilibrada entre potència, autonomia i cost.  
Permet protegir els equips crítics de TecnoGestió S.L. i garanteix la continuïtat de servei davant incidències elèctriques.

---


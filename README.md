import React from 'react';
import { ScrollView, View, Text, TextInput, Button, TouchableOpacity, StyleSheet } from 'react-native';
import { Camera, Video } from 'expo-camera';
import { MaterialIcons, Feather, FontAwesome } from '@expo/vector-icons';


export default function ContainerInspectionApp() {
  return (
    <ScrollView style={styles.container} contentContainerStyle={{ padding: 16 }}>
      <Text style={styles.header}>🚢 Container Inspection</Text>


      {/* Step 1: Container ID */}
      <View style={styles.card}>
        <Text style={styles.cardHeader}><FontAwesome name="cube" size={24} color="#1E40AF" /> Scan / Enter Container ID</Text>
        <TextInput style={styles.input} placeholder="Enter container number" />
        <Button title="Scan QR/Barcode" onPress={() => {}} />
      </View>


      {/* Step 2: Photos */}
      <View style={styles.card}>
        <Text style={styles.cardHeader}><MaterialIcons name="camera-alt" size={24} color="#059669" /> Take Photos</Text>
        <Text style={styles.cardText}>Capture all sides of the container to check for dents, rust, cracks, and damage.</Text>
        <View style={styles.grid}>
          {['Front', 'Back', 'Left', 'Right', 'Roof', 'Floor'].map(side => (
            <TouchableOpacity key={side} style={styles.button}><Text>📸 {side}</Text></TouchableOpacity>
          ))}
        </View>
      </View>


      {/* Step 2b: Video Capture */}
      <View style={styles.card}>
        <Text style={styles.cardHeader}><Feather name="video" size={24} color="#DC2626" /> Record Video</Text>
        <Text style={styles.cardText}>Record a walk-around video for AI-powered defect detection.</Text>
        <Button title="🎥 Start Recording" onPress={() => {}} />
        <Button title="Upload Existing Video" onPress={() => {}} />
      </View>


      {/* Step 2c: AI Analysis Results */}
      <View style={[styles.card, styles.aiCard]}>
        <Text style={styles.cardHeader}><MaterialIcons name="report-problem" size={24} color="#F97316" /> AI Analysis Results</Text>
        <Text style={styles.cardText}>Automated defect detection based on uploaded photos and video.</Text>
        <View style={styles.resultItem}><MaterialIcons name="report-problem" size={20} color="#B45309" /><Text> Severe dent detected on left side panel.</Text></View>
        <View style={styles.resultItem}><MaterialIcons name="report-problem" size={20} color="#D97706" /><Text> Moderate rust patch on roof corner.</Text></View>
        <View style={styles.resultItem}><MaterialIcons name="check-circle" size={20} color="#059669" /><Text> No issues detected on door and locking system.</Text></View>
      </View>


      {/* Step 3: Inspection Checklist */}
      <View style={styles.card}>
        <Text style={styles.cardHeader}><MaterialIcons name="check-box" size={24} color="#CA8A04" /> Inspection Checklist</Text>
        {['Doors & locks intact', 'No major dents or cracks', 'No visible rust', 'Floor & roof stable', 'Seal in place'].map(item => (
          <View key={item} style={styles.checkboxItem}><Text>⬜ {item}</Text></View>
        ))}
      </View>


      {/* Step 4: Report */}
      <View style={styles.card}>
        <Text style={styles.cardHeader}><MaterialIcons name="description" size={24} color="#7C3AED" /> Generate Report</Text>
        <Text style={styles.cardText}>Once complete, generate a detailed report with photos, video, AI results, and checklist outcomes.</Text>
        <Button title="Generate PDF Report" onPress={() => {}} />
      </View>
    </ScrollView>
  );
}


const styles = StyleSheet.create({
  container: { flex: 1, backgroundColor: '#F3F4F6' },
  header: { fontSize: 28, fontWeight: 'bold', textAlign: 'center', marginBottom: 16 },
  card: { backgroundColor: '#FFFFFF', borderRadius: 16, padding: 16, marginBottom: 16, shadowColor: '#000', shadowOpacity: 0.1, shadowRadius: 5, elevation: 3 },
  cardHeader: { fontSize: 18, fontWeight: '600', marginBottom: 8 },
  cardText: { color: '#6B7280', fontSize: 14, marginBottom: 8 },
  input: { borderWidth: 1, borderColor: '#D1D5DB', borderRadius: 8, padding: 8, marginBottom: 8 },
  grid: { flexDirection: 'row', flexWrap: 'wrap', gap: 8 },
  button: { backgroundColor: '#E5E7EB', padding: 12, borderRadius: 8, margin: 4 },
  aiCard: { borderWidth: 1, borderColor: '#D1D5DB', borderStyle: 'dashed' },
  resultItem: { flexDirection: 'row', alignItems: 'center', gap: 4, paddingVertical: 4 },
  checkboxItem: { paddingVertical: 4 }
});
